# 🏥 CodeHealth CI/CD Pipeline

## 📘 Descrição do Projeto
Este projeto foi desenvolvido como parte do estudo dos princípios de **Integração Contínua (CI)**, **Entrega Contínua (CD)** e **Gerência de Configuração**, aplicados em um cenário fictício da startup **CodeHealth**, que está desenvolvendo um sistema web de **agendamento médico**.

O objetivo é criar um pipeline simples de CI/CD utilizando **GitHub Actions**, garantindo que cada atualização de código seja **testada**, **validada** e **implantada com segurança**.

---

## 🚀 Descrição do Pipeline

O pipeline foi configurado no arquivo `.github/workflows/ci.yml` e é executado **automaticamente a cada push na branch `develop`**.  
Ele é composto pelas seguintes etapas:

1. **Checkout do código**  
   - Obtém o código da branch atual no repositório GitHub.

2. **Build (Simulação)**  
   - Executa um comando `echo "Gerando artefato de homologação..."` simulando a etapa de compilação.

3. **Testes (Simulação)**  
   - Simula execução de testes automatizados com `echo "Running tests..."`.  
   - Caso os testes falhem, a execução do pipeline é interrompida.

4. **Relatório de Status**  
   - Exibe no log o resultado da execução: “Build successful” ou “Test failed”.

5. **Deploy Simulado (Entrega Contínua)**  
   - Caso os testes passem com sucesso, o pipeline gera um artefato `.zip` com os arquivos do projeto, representando a entrega para um ambiente de **homologação (`staging/`)**.
   - Essa etapa é condicional, só executada se o job de testes for bem-sucedido.

**Gatilhos do Pipeline**
```yaml
on:
  push:
    branches:
      - develop
O workflow é executado automaticamente sempre que há um push na branch develop.

Estrutura de Branches
O controle de versão segue o modelo Git Flow simplificado:

Branch	Função	Descrição
main	Produção	Contém o código estável e pronto para deploy em produção.
develop	Integração	Local onde novas funcionalidades são integradas e testadas continuamente.
feature/teste-ci	Funcionalidade temporária	Usada para desenvolver e testar novas features antes de integrá-las na develop.

Fluxo de trabalho:

bash
Copiar código
feature/teste-ci → develop → main
Pull Requests são utilizados para revisar e aprovar merges entre branches.

Estrutura do Projeto
css
Copiar código
codehealth-ci-cd-nome-sobrenome/
├── .github/
│   └── workflows/
│       └── ci.yml
├── index.html
├── .gitignore
├── .env.example
├── README.md
└── staging/
    └── build.zip (gerado automaticamente no pipeline)
Screenshot da Execução do Workflow
(Substitua o link abaixo pela imagem do print real da execução no GitHub Actions)


Exemplo de execução bem-sucedida mostrando as etapas de build, test e deploy.

🔒 Boas Práticas Aplicadas de Segurança e Configuração
Arquivo .env e variáveis de ambiente

Foi criado um arquivo config.env contendo variáveis simuladas como:

env
Copiar código
DB_USER=meu_usuario
DB_PASS=minha_senha123
Este arquivo não é versionado e está listado no .gitignore.

Motivo:
Evita o vazamento de credenciais sensíveis no controle de versão público.

Uso do .gitignore

Arquivos e diretórios que não devem ser versionados:

arduino
Copiar código
config.env
staging/
__pycache__/
node_modules/
Garante que apenas o código-fonte essencial seja armazenado no repositório.

GitHub Secrets

Uma variável simulada DEPLOY_KEY foi armazenada com segurança em Settings → Secrets and variables → Actions.

Essa chave é usada de forma segura pelo workflow, sem exposição no código.

Exemplo de acesso no pipeline:

yaml
Copiar código
- name: Simular Deploy com Secret
  run: echo "Usando chave de deploy: ${{ secrets.DEPLOY_KEY }}"
Controle de Branches

As merges em main são realizadas apenas via Pull Requests revisados.

Mantém a integridade e rastreabilidade das versões de produção.

🧠 Conclusão
O pipeline desenvolvido permite:

Automatizar a integração e validação de código.

Reduzir falhas humanas durante o deploy.

Garantir segurança e rastreabilidade através de boas práticas DevOps.

Com essa base, o projeto CodeHealth pode evoluir para uma pipeline real de deploy em ambiente de produção com apenas pequenas adaptações.

👤 Autor
Nome: Seu Nome Sobrenome
Repositório: codehealth-ci-cd-nome-sobrenome
