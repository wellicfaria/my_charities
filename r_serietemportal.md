# Exemplo em R

Suponha que temos três séries temporais, chamadas "s1", "s2" e "s3". Podemos ler esses dados em um dataframe e depois converter as colunas em séries temporais usando a função ts:

```R
# Lendo os dados
dados <- read.csv("dados.csv")

# Convertendo as colunas em séries temporais
s1 <- ts(dados$s1, start = c(2000, 1), frequency = 12)
s2 <- ts(dados$s2, start = c(2000, 1), frequency = 12)
s3 <- ts(dados$s3, start = c(2000, 1), frequency = 12)

```

Em seguida, podemos plotar as três séries temporais juntas para visualizá-las:


```R

# Plotando as três séries temporais
plot(s1, col = "red", main = "Três Séries Temporais")
lines(s2, col = "blue")
lines(s3, col = "green")
legend("topright", c("s1", "s2", "s3"), col = c("red", "blue", "green"), lty = 1)

```

Agora, podemos calcular as estatísticas descritivas básicas de cada série temporal usando a função summary:

```R
# Calculando as estatísticas descritivas básicas de cada série temporal
summary(s1)
summary(s2)
summary(s3)
```

Além disso, podemos ajustar um modelo de série temporal ARIMA em cada série temporal usando a função arima:

```R
# Ajustando um modelo ARIMA em cada série temporal
modelo_s1 <- arima(s1, order = c(1, 1, 1))
modelo_s2 <- arima(s2, order = c(0, 1, 1))
modelo_s3 <- arima(s3, order = c(1, 0, 1))
```

Finalmente, podemos fazer previsões de cada série temporal usando os modelos ARIMA ajustados usando a função forecast:

```R
# Fazendo previsões de cada série temporal usando os modelos ARIMA ajustados
previsao_s1 <- forecast(modelo_s1, h = 12)
previsao_s2 <- forecast(modelo_s2, h = 12)
previsao_s3 <- forecast(modelo_s3, h = 12)

# Plotando as previsões de cada série temporal
plot(previsao_s1, main = "Previsão das Três Séries Temporais")
lines(previsao_s2$mean, col = "blue")
lines(previsao_s3$mean, col = "green")
legend("topright", c("s1", "s2", "s3"), col = c("red", "blue", "green"), lty = 1)
```

Este é apenas um exemplo básico de como analisar mais de uma série temporal em R. Dependendo do objetivo da análise, outras técnicas e métodos podem ser usados.

# Exemplo em Python

```R
# Importando a biblioteca pandas
import pandas as pd

# Importando a biblioteca matplotlib
import matplotlib.pyplot as plt

# Lendo os dados
dados = pd.read_csv("dados.csv")

# Convertendo as colunas em séries temporais
s1 = pd.Series(dados['s1'], index=pd.date_range(start='2000-01-01', periods=len(dados), freq='M'))
s2 = pd.Series(dados['s2'], index=pd.date_range(start='2000-01-01', periods=len(dados), freq='M'))
s3 = pd.Series(dados['s3'], index=pd.date_range(start='2000-01-01', periods=len(dados), freq='M'))


# Plotando as três séries temporais
plt.plot(s1, color='red', label='s1')
plt.plot(s2, color='blue', label='s2')
plt.plot(s3, color='green', label='s3')
plt.legend()
plt.title('Três Séries Temporais')
plt.show()

# Calculando as estatísticas descritivas básicas de cada série temporal
print(s1.describe())
print(s2.describe())
print(s3.describe())

# Importando a biblioteca statsmodels
import statsmodels.api as sm

# Ajustando um modelo ARIMA em cada série temporal
modelo_s1 = sm.tsa.arima.ARIMA(s1, order=(1, 1, 1)).fit()
modelo_s2 = sm.tsa.arima.ARIMA(s2, order=(0, 1, 1)).fit()
modelo_s3 = sm.tsa.arima.ARIMA(s3, order=(1, 0, 1)).fit()


# Fazendo previsões de cada série temporal usando os modelos ARIMA ajustados
previsao_s1 = modelo_s1.forecast(steps=12)
previsao_s2 = modelo_s2.forecast(steps=12)
previsao_s3 = modelo_s3.forecast(steps=12)

# Plotando as previsões de cada série temporal
plt.plot(s1, color='red', label='s1')
plt.plot(previsao_s1, color='red', linestyle='dashed')
plt.plot(s2, color='blue', label='s2')
plt.plot(previsao_s2, color='blue', linestyle='dashed')
plt.plot(s3, color='green', label='s3')
plt.plot(previsao_s3, color='green', linestyle='dashed')
plt.legend()
plt.title('Previsão das Três Séries Temporais')
plt.show()


```
