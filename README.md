# Explorando Workflows Automatizados com AWS Step Functions

## 📋 Descrição do Projeto
Este repositório foi criado para o desafio de documentação técnica sobre orquestração de serviços utilizando o **AWS Step Functions**. O objetivo principal é demonstrar como criar workflows automatizados, gerenciar estados e integrar diferentes serviços da AWS de forma visual e estruturada.

## 🚀 O que são AWS Step Functions?
O AWS Step Functions é um serviço de orquestração de fluxos de trabalho baseado em máquinas de estado. Ele permite conectar serviços como AWS Lambda, Amazon SQS, Amazon SNS, entre outros, simplificando a construção de aplicações distribuídas e microsserviços.

## ⚙️ Arquitetura do Workflow
Abaixo está a representação visual da máquina de estados criada para este desafio:

![Workflow da Máquina de Estados](./imagens/seu-print-do-workflow.png)

### Explicação dos Estados:
1. **Estado Inicial (Start):** Gatilho que inicia a execução do fluxo.
2. **Estado de Escolha (Choice):** Avalia as condições dos dados de entrada para direcionar o fluxo.
3. **Estado de Execução (Task):** Executa uma ação específica (ex: chama uma função Lambda).
4. **Estado de Sucesso/Falha (Pass/Fail):** Finaliza a execução do fluxo informando o resultado.

## 🛠️ Código Amazon States Language (ASL)
Caso queira visualizar ou replicar a máquina de estados, utilize o código JSON abaixo no console do AWS Step Functions:

```json
{
  "Comment": "Exemplo de máquina de estados para automação",
  "StartAt": "VerificarDados",
  "States": {
    "VerificarDados": {
      "Type": "Choice",
      "Choices": [
        {
          "Variable": "\$.status",
          "StringEquals": "aprovado",
          "Next": "ProcessarSucesso"
        }
      ],
      "Default": "NotificarErro"
    },
    "ProcessarSucesso": {
      "Type": "Pass",
      "End": true
    },
    "NotificarErro": {
      "Type": "Fail",
      "Error": "StatusInvalido",
      "Cause": "O status fornecido não foi aprovado."
    }
  }
}
```

## 🧠 Aprendizados e Experiência
Durante o desenvolvimento deste desafio, foi possível compreender:
- A importância da orquestração visual para debugar erros em sistemas distribuídos.
- Como o tratamento de erros nativo do Step Functions reduz a necessidade de código complexo.
- A sintaxe básica do Amazon States Language (ASL).

## 📚 Links Úteis Utilizados
- [Documentação Oficial do AWS Step Functions](https://amazon.com)
- [Guia de Markdown do GitHub](https://github.com)
