# 🤖 Chatbot de Clima - Telegram + N8N

Bot do Telegram que retorna informações meteorológicas em tempo real usando a API do OpenWeather.

## 📋 Descrição do Projeto

Este projeto implementa um chatbot no Telegram utilizando N8N para automação de workflow. O bot recebe o nome de uma cidade e retorna a temperatura atual em graus Celsius (°C), com mensagens amigáveis em português.

### Funcionalidades

- 🌤️ Consulta de temperatura em tempo real
- 🌍 Suporte a cidades brasileiras e internacionais
- 🇧🇷 Mensagens em português
- ✅ Validação de entrada e tratamento de erros
- 📱 Interface via Telegram

## 🛠️ Tecnologias Utilizadas

- **N8N**: Plataforma de automação de workflows
- **Telegram Bot API**: Interface de comunicação com usuários
- **OpenWeather API**: Dados meteorológicos em tempo real

## 📦 Pré-requisitos

Antes de começar, você precisará:

1. **N8N instalado e rodando**
   - Pode ser self-hosted ou na nuvem
   - Acesso ao painel administrativo

2. **Bot do Telegram criado**
   - Token do bot via [@BotFather](https://t.me/botfather)

3. **Chave da API OpenWeather**
   - Conta gratuita em [OpenWeather](https://openweathermap.org/api)
   - API Key gerada

## 🚀 Passo a Passo para Configuração

### 1️⃣ Criar o Bot no Telegram

1. Abra o Telegram e procure por `@BotFather`
2. Envie o comando `/newbot`
3. Escolha um nome para seu bot (ex.: "Clima Bot")
4. Escolha um username único (ex.: "MeuClimaBot")
5. **Copie e guarde o token fornecido** (formato: `123456789:ABCdefGHIjklMNOpqrsTUVwxyz`)

### 2️⃣ Obter a Chave da API OpenWeather

1. Acesse [OpenWeather](https://openweathermap.org/api)
2. Crie uma conta gratuita
3. Vá em "API keys" no seu perfil
4. Copie a chave padrão ou crie uma nova
5. **Guarde a API Key** (formato: `c960954fba928ba8167047ccc03766ae`)

### 3️⃣ Importar o Workflow no N8N

1. Acesse seu painel do N8N
2. Clique no menu (**☰**) no canto superior esquerdo
3. Selecione **"Import from File"** ou **"Import Workflow"**
4. Escolha o arquivo JSON do workflow fornecido
5. Clique em **"Import"**

### 4️⃣ Configurar Credenciais no N8N

#### Configurar Telegram Bot

1. No workflow importado, clique no nó **"Telegram Trigger"**
2. Na seção **Credentials**, clique em **"Create New Credential"**
3. Preencha os dados:
   - **Credential Name**: `Telegram account` (ou nome de sua preferência)
   - **Access Token**: Cole o token do seu bot do Telegram
4. Clique em **"Save"**
5. Repita o processo para os nós:
   - **"Send a text message"**
   - **"Send a text message1"**

#### Configurar OpenWeather API

1. No workflow, clique no nó **"HTTP Request"**
2. Localize o parâmetro `appid` na seção **Query Parameters**
3. Substitua o valor pela sua **OPENWEATHER_API_KEY**
4. Clique em **"Save"** ou **"Execute Workflow"** para salvar as alterações

### 5️⃣ Ativar o Workflow

1. No topo da tela do workflow, certifique-se de que o toggle **"Active"** está ligado (verde)
2. Verifique se todos os nós estão conectados corretamente
3. O workflow agora está pronto para receber mensagens!

## 🧪 Como Testar o Chatbot

### Exemplos de Uso

Abra o Telegram e envie mensagens para o seu bot:

#### ✅ Casos de Sucesso

```
Você: São Paulo,SP
Bot: 🌤️ A temperatura em São Paulo é de 23°C.

Você: Rio de Janeiro,RJ
Bot: 🌤️ A temperatura em Rio de Janeiro é de 28°C.

Você: London,UK
Bot: 🌤️ A temperatura em London é de 15°C.
```

#### ❌ Casos de Erro

```
Você: Cidade Inexistente
Bot: ❌ Cidade não encontrada. Use o formato Cidade,UF (ex.: São Paulo,SP).

Você: xyzabc
Bot: ❌ Cidade não encontrada. Use o formato Cidade,UF (ex.: São Paulo,SP).
```

### Formato Esperado

- **Cidades brasileiras**: `Cidade,UF` (ex.: `Curitiba,PR`)
- **Cidades internacionais**: `Cidade,País` (ex.: `Paris,FR`)
- **Apenas cidade**: `Cidade` (pode funcionar para cidades grandes)


## 🔧 Variáveis de Ambiente

| Variável                | Descrição                          
|-------------------------|------------------------------------
| `TELEGRAM_BOT_TOKEN`    | Token do bot do Telegram           
| `OPENWEATHER_API_KEY`   | Chave da API OpenWeather           

