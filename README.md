# PRAKTIKUM-KOMNUM-KEL-11


<img width="812" height="306" alt="image" src="https://github.com/user-attachments/assets/4e713a00-f6dc-48c1-b652-de0edd5300b5" />

### PRAKTIKUM 1 (PPT 2)
```
import numpy as np
import matplotlib.pyplot as plt

def regula_falsi_method(func, a, b, tol=1e-5, max_iter=100):
    if func(a) * func(b) >= 0:
        print("Error: f(a) dan f(b) harus beda tanda")
        return None

    print(f"{'Iterasi':<10} | {'a':<10} | {'b':<10} | {'c (akar)':<10} | {'f(c)':<15}")
    print("-" * 65)

    for i in range(1, max_iter + 1):
        fa = func(a)
        fb = func(b)

        c = (a * fb - b * fa) / (fb - fa)
        fc = func(c)

        print(f"{i:<10} | {a:<10.5f} | {b:<10.5f} | {c:<10.5f} | {fc:<15.5f}")

        if abs(fc) < tol:
            print("-" * 65)
            print(f"Akar ditemukan pada x = {c:.5f} setelah {i} iterasi.")
            return c

        if fa * fc < 0:
            b = c
        else:
            a = c

    return c

def plot_function(func, a, b, root):
    x_vals = np.linspace(a - 1, b + 1, 400)
    y_vals = func(x_vals)

    plt.plot(x_vals, y_vals, label='f(x)')
    plt.axhline(0, linestyle='--')

    if root:
        plt.plot(root, func(root), 'ro', label=f'Akar (x={root:.4f})')

    plt.title("Grafik Metode Regula Falsi")
    plt.legend()
    plt.grid()
    plt.show()

def f(x):
    return np.exp(-x) - x

a = 0
b = 1

akar = regula_falsi_method(f, a, b)

if akar:
    plot_function(f, a, b, akar)
```

- Output
<img width="728" height="282" alt="image" src="https://github.com/user-attachments/assets/ee267278-f45e-42fe-adf5-bf8cabbb5fc7" />

- Grafik Fungsi
<img width="640" height="480" alt="WhatsApp Image 2026-04-29 at 16 12 21" src="https://github.com/user-attachments/assets/dcca1b6c-3314-4a6b-af80-8f7f0b5dd5f4" />
