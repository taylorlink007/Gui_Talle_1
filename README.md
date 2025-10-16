# 🧠 Taller: Análisis de Datos con Pandas, NumPy y Matplotlib  

**Asignatura:** Inteligencia Artificial  
**Integrantes:**  
- Jhan Carlos Zamora Nuñez  
- Taylor Antonio Quiñones Caicedo  
- Gilary Daniela Vargas Hurtado  
- Esteban David Ruiz Caicedo  

---

## 🎯 **Objetivo del Taller**

El objetivo de este taller es aplicar herramientas fundamentales para el **análisis de datos en Python**, utilizando las librerías **NumPy, Pandas, Matplotlib y SciPy**.  
A través de datos sintéticos, se busca comprender cómo generar, manipular, analizar y visualizar información cuantitativa, desarrollando habilidades esenciales para el trabajo con datos en el campo de la **Inteligencia Artificial**.

---

## 📋 **Descripción General**

En este taller se realizan operaciones básicas de análisis estadístico y visualización de datos.  
Se implementan conceptos como:
- Generación de arreglos numéricos.
- Cálculo de medidas estadísticas (media, mediana, moda, varianza y desviación estándar).
- Creación y filtrado de DataFrames.
- Representación gráfica mediante diagramas de barras, dispersión e histogramas.
- Agrupación y análisis comparativo de datos categóricos.

---

## 💻 **Código Completo y Explicado**

```python
# ===========================================
# 🧠 Taller: Análisis de Datos con Pandas, NumPy y Matplotlib
# ===========================================

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from scipy import stats

# ===========================================
# 1️⃣ Crear un arreglo con los números del 1 al 1000 y calcular su suma total
# ===========================================
arreglo = np.arange(1, 1001)
suma_total = np.sum(arreglo)
print("Suma total de los elementos:", suma_total)
# Explicación: np.arange genera una secuencia de números del 1 al 1000.
# np.sum calcula la suma total de todos los elementos del arreglo.


# ===========================================
# 2️⃣ Calcular la media, mediana y moda del arreglo [2,4,4,6,8,8,8,10]
# ===========================================
datos = np.array([2, 4, 4, 6, 8, 8, 8, 10])

media = np.mean(datos)
mediana = np.median(datos)
moda = stats.mode(datos, keepdims=True)[0][0]

print("Media:", media)
print("Mediana:", mediana)
print("Moda:", moda)
# Explicación:
# Media -> promedio aritmético de los datos.
# Mediana -> valor central del conjunto ordenado.
# Moda -> valor que más se repite en el conjunto.


# ===========================================
# 3️⃣ Calcular la varianza y desviación estándar del mismo conjunto
# ===========================================
varianza = np.var(datos)
desviacion = np.std(datos)

print("Varianza:", varianza)
print("Desviación estándar:", desviacion)
# Explicación:
# La varianza mide la dispersión de los datos respecto a la media.
# La desviación estándar es la raíz cuadrada de la varianza, indicando cuánto varían los datos.


# ===========================================
# 4️⃣ Crear un DataFrame con las columnas Nombre, Edad y Nota
# ===========================================
datos_estudiantes = {
    "Nombre": ["Ana", "Luis", "Sofía", "Carlos", "María"],
    "Edad": [20, 22, 21, 23, 20],
    "Nota": [3.5, 4.8, 4.2, 3.9, 4.5]
}

df = pd.DataFrame(datos_estudiantes)
print(df)
# Explicación: Se construye un DataFrame con información simulada de estudiantes.


# ===========================================
# 5️⃣ Calcular la media, mínima, máxima y desviación estándar de las notas
# ===========================================
media_nota = df["Nota"].mean()
min_nota = df["Nota"].min()
max_nota = df["Nota"].max()
desv_nota = df["Nota"].std()

print("Media:", media_nota)
print("Mínima:", min_nota)
print("Máxima:", max_nota)
print("Desviación estándar:", desv_nota)
# Explicación: Se aplican métodos estadísticos de Pandas sobre la columna “Nota”.


# ===========================================
# 6️⃣ Filtrar los estudiantes con nota mayor o igual a 4.0
# ===========================================
df_filtrado = df[df["Nota"] >= 4.0]
print("Estudiantes con nota >= 4.0:")
print(df_filtrado)
# Explicación: Se usa una condición lógica para filtrar los registros del DataFrame.


# ===========================================
# 7️⃣ Gráfico de barras con las notas de los estudiantes
# ===========================================
plt.bar(df["Nombre"], df["Nota"])
plt.title("Notas de los estudiantes")
plt.xlabel("Nombre")
plt.ylabel("Nota")
plt.show()
# Explicación: El gráfico de barras permite visualizar comparativamente las notas.


# ===========================================
# 8️⃣ Gráfico de dispersión entre Edad y Nota
# ===========================================
plt.scatter(df["Edad"], df["Nota"])
plt.title("Relación entre Edad y Nota")
plt.xlabel("Edad")
plt.ylabel("Nota")
plt.show()
# Explicación: El diagrama de dispersión muestra si existe relación entre la edad y la nota.


# ===========================================
# 9️⃣ Agregar una columna de Género y calcular el promedio de notas por género
# ===========================================
df["Género"] = ["F", "M", "F", "M", "F"]

promedio_genero = df.groupby("Género")["Nota"].mean()
print("Promedio de notas por género:")
print(promedio_genero)
# Explicación: Se agrupan los datos por género para obtener el promedio de cada grupo.


# ===========================================
# 🔟 Calcular el rango, varianza y desviación estándar de las notas + histograma
# ===========================================
rango = df["Nota"].max() - df["Nota"].min()
varianza = df["Nota"].var()
desviacion = df["Nota"].std()

print("Rango:", rango)
print("Varianza:", varianza)
print("Desviación estándar:", desviacion)

# Histograma
plt.hist(df["Nota"], bins=5, edgecolor="black")
plt.title("Distribución de las Notas")
plt.xlabel("Nota")
plt.ylabel("Frecuencia")
plt.show()
# Explicación: El histograma muestra cómo se distribuyen las calificaciones en intervalos.

# ===========================================
# 💾 Exportar los datos a Excel
# ===========================================
df.to_excel("taller_analisis_datos.xlsx", index=False)
print("Archivo Excel generado correctamente.")
# Explicación: Se guarda el DataFrame en un archivo Excel para conservar y compartir los resultados.
