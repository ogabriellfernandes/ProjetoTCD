# 📊 Bank Marketing — Previsão de Assinatura de Depósito

## O que é esse projeto?

Esse projeto usa dados de uma campanha de telemarketing de um banco português
para tentar prever se um cliente vai assinar um depósito a prazo ou não.

Em outras palavras: com base nas informações do cliente e da ligação,
o modelo tenta responder → **"Vale a pena ligar pra essa pessoa?"**

---

## Qual problema estamos resolvendo?

O banco faz muitas ligações, mas poucos clientes dizem sim (~11%).
Isso significa que a maioria das ligações é desperdiçada.

Com um modelo de machine learning, conseguimos:
- Identificar quais clientes têm mais chance de dizer sim
- Reduzir ligações desnecessárias
- Aumentar a taxa de conversão da campanha

---

## De onde vieram os dados?

- **Dataset:** Bank Marketing Dataset
- **Fonte:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Bank+Marketing)
- **Arquivo usado:** `bank-additional-full.csv`
- **Tamanho:** ~41.000 linhas e 21 colunas

---

## Quais ferramentas foram usadas?

| Ferramenta | Para que serve |
|---|---|
| Python | Linguagem principal |
| Pandas | Manipulação de dados |
| Matplotlib / Seaborn | Gráficos |
| Scikit-learn | Modelos de machine learning |
| Joblib | Salvar e carregar o modelo |
| Jupyter Notebook | Ambiente de desenvolvimento |

---

## Qual foi o caminho do projeto?

### 01 — Análise Exploratória (EDA)
- Carreguei e entendi os dados
- Verifiquei valores nulos e duplicados
- Analisei a coluna alvo `y` (sim ou não)
- Vi quais categorias e meses tinham mais conversão
- Removi a coluna `duration` (ela só existe após a ligação)

### 02 — Preparação dos Dados
- Substituí valores `unknown` pela categoria mais comum
- Transformei colunas de texto em números (One-Hot Encoding)
- Dividi os dados em treino (80%) e teste (20%)
- Coloquei os números na mesma escala (StandardScaler)

### 03 — Modelagem
- Treinei dois modelos: **Regressão Logística** e **Random Forest**
- Comparei os dois usando F1-Score e ROC-AUC
- O **Random Forest** teve melhor desempenho e foi salvo

### 04 — Conclusão
- Carreguei o modelo salvo
- Fiz as previsões finais no conjunto de teste
- Analisei os acertos, erros e tipos de falha
- Listei os clientes com maior probabilidade de assinar

---

## Quais foram os resultados?

| Métrica | Valor |
|---|---|
| Modelo | Random Forest |
| ROC-AUC | ~0.93 |
| F1-Score (classe 1) | ~0.63 |
| Precision | ~0.67 |
| Recall | ~0.59 |

> Os valores exatos aparecem no notebook `04_conclusao.ipynb`

---

## O que aprendi com esse projeto?

- Quando os dados são desbalanceados (muito mais "não" do que "sim"),
  a acurácia não é uma boa métrica — usei o **F1-Score**

- A coluna `duration` parecia muito boa, mas não pode ser usada
  porque ela só existe **depois** que a ligação acontece

- O **Random Forest** foi melhor que a Regressão Logística
  porque consegue capturar relações mais complexas nos dados

- As variáveis mais importantes foram relacionadas a:
  - Contato anterior com o cliente
  - Mês e dia da semana da ligação
  - Indicadores econômicos do período

---

## Como rodar esse projeto?

### 1. Clonar o repositório
```bash
git clone https://github.com/ogabriellfernandes/ProjetoTCD.git
cd ProjetoTCD
```

### 2. Instalar as dependências
```bash
pip install -r requirements.txt
```

### 3. Rodar os notebooks em ordem
```bash
jupyter notebook
```

Abra e execute na ordem:
1. `01_eda.ipynb`
2. `02_feature_engineering.ipynb`
3. `03_modelagem.ipynb`
4. `04_conclusao.ipynb`