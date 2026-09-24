# ☁️ Cloud Computing - Aula 01: Introdução e Paradigma Tradicional

> 💡 **Foco SAA-C03:** Embora a prova foque em arquitetura técnica, os conceitos fundamentais de "por que ir para a nuvem" baseiam muitas questões, principalmente no que diz respeito à troca de **CapEx** por **OpEx**.

## 🏢 1. Como era antes da Nuvem? (Modelo On-Premises Tradicional)
Antes da computação em nuvem, as empresas precisavam construir e manter seus próprios Data Centers locais (On-Premises). Isso trazia grandes desafios:

* **Altos Custos Iniciais (CapEx - Capital Expenditure):** Era necessário gastar milhões antecipadamente comprando servidores físicos, racks, switches e cabos antes mesmo do projeto começar a dar lucro.
* **Adivinhação de Capacidade (Guessing Capacity):** Você tinha que prever o tráfego máximo (ex: Black Friday). Se comprasse servidores de menos, o site caía. Se comprasse a mais, eles ficavam ociosos acumulando poeira no resto do ano, desperdiçando dinheiro.
* **Ciclos de Inovação Lentos:** Comprar, importar, instalar e configurar um novo servidor físico podia levar semanas ou meses, travando a agilidade dos desenvolvedores.
* **Manutenção Pesada (Undifferentiated Heavy Lifting):** A equipe de TI gastava muito tempo e dinheiro com energia elétrica, resfriamento físico (ar-condicionado), segurança do prédio e troca de discos queimados, em vez de focar no software em si.

---

## 🌩️ 2. O que é Cloud Computing? (A Solução)
**Definição AWS:** É a entrega sob demanda de poder computacional, banco de dados, armazenamento, aplicações e outros recursos de TI por meio da internet, com um modelo de preço pago conforme o uso (*Pay-as-you-go*).

Basicamente, você aluga os computadores de outra pessoa (neste caso, da AWS) e acessa tudo via internet.

### 🌟 As Grandes Vantagens (Por que migrar?)
1. **Trocar CapEx por OpEx (Operational Expenditure):** Você para de investir dinheiro em hardware físico (CapEx) e passa a pagar apenas pelo que consome mensalmente (OpEx), como se fosse uma conta de água ou luz.
2. **Economia de Escala (Economies of Scale):** Como a AWS atende centenas de milhares de clientes, ela compra hardware em quantidades globais. Isso reduz brutalmente o custo por unidade, e ela repassa essa economia para você em forma de preços menores.
3. **Fim da Adivinhação de Capacidade:** Você escala (*Scale Out / Scale In*) exatamente conforme a demanda, pagando apenas pela capacidade real utilizada no momento.
4. **Agilidade e Velocidade:** Você consegue subir centenas de servidores (*EC2*) em questão de minutos com poucos cliques, permitindo experimentação e inovação rápidas.
5. **Alcance Global em Minutos:** Você pode implantar sua aplicação em várias regiões ao redor do mundo (EUA, Europa, Japão, Brasil) simultaneamente, entregando baixíssima latência para clientes globais.

# ☁️ Cloud Computing - Aula 02: Benefícios e Exemplos Práticos

Na nuvem da AWS, os benefícios vão muito além de "não ter um servidor em casa". Eles mudam a forma como as empresas operam.

## 🚀 1. Velocidade (Agilidade)
- **O que é:** Na AWS, chamamos isso de **Agilidade (Agility)**. Em vez de esperar semanas pela aprovação de compra, frete e instalação de um servidor físico, você provisiona milhares de servidores em **segundos ou minutos** com poucos cliques.
- **Benefício de Negócio:** Reduz o *Time-to-Market* (tempo de lançamento). A equipe de desenvolvimento pode testar ideias novas rapidamente, falhar rápido e sem custos altíssimos de infraestrutura.

## 🔄 2. Updates (Atualizações sem interrupção)
- **Serviços Gerenciados (Managed Services):** Em serviços como o Amazon RDS (Banco de Dados) ou DynamoDB, a própria AWS cuida das atualizações de sistema operacional e aplicação de patches de segurança de forma invisível.
- **Deployments (CI/CD):** Usando serviços de nuvem, arquiteturas modernas permitem técnicas como *Blue/Green Deployment* (subir uma versão nova inteira do site ao lado da antiga e apenas "virar a chave" do tráfego). Resultado: **Zero Downtime** (zero tempo de inatividade para o cliente) durante as atualizações.

## 💸 3. Custo (Baixo e Flexível)
- **Pay-as-you-go:** Você paga como uma conta de luz. Só paga pelo que usar e pelo tempo exato que usar.
- **Fim da Ociosidade:** Você não paga por servidores decolando calor de madrugada se ninguém estiver acessando o site. Se a máquina for desligada, a cobrança de processamento para.
- **Economia de Escala:** A AWS reduz os preços constantemente devido ao volume massivo de clientes globais que compartilham a mesma infraestrutura física.

## 🔒 4. Data Security (Segurança de Dados)
A AWS adota a postura de que a nuvem é mais segura que a maioria dos data centers locais.
- **Modelo de Responsabilidade Compartilhada (Certeza de Prova!):** 
  - *Segurança DA Nuvem (AWS):* A AWS protege os cabos, os data centers físicos, os geradores, os hypervisors e o hardware.
  - *Segurança NA Nuvem (Cliente):* Você é responsável por quem acessa seus dados (IAM), quais portas estão abertas (Security Groups) e por ativar a Criptografia (ex: encriptação no S3).
- **Compliance Global:** Data centers com segurança de nível militar, certificações de conformidade automáticas (HIPAA, PCI-DSS, SOC).

---

## 📈 5. Scalability (Escalabilidade na Prática)

A capacidade do sistema de crescer ou encolher para atender à demanda. Na prova, você precisa saber diferenciar os dois tipos:

### ⬆️ Escalabilidade Vertical (Scale UP / Scale DOWN)
- **Conceito:** Aumentar ou diminuir a "potência" de uma única máquina (mais CPU, mais RAM).
- **Limitação:** Tem um teto (chega um ponto onde não existe um processador mais potente no mundo para comprar) e normalmente exige reiniciar a máquina (Downtime).
- **Exemplo Prático:** 
  - Você tem um banco de dados rodando em uma instância `t2.micro` (1 GB de RAM) que está travando.
  - Você para a instância e muda o tipo para `m5.large` (8 GB de RAM). O banco passa a aguentar a carga. 

### ➡️ Escalabilidade Horizontal (Scale OUT / Scale IN)
- **Conceito:** Aumentar ou diminuir a "quantidade" de máquinas trabalhando juntas (distribuindo o peso).
- **Vantagem:** É o pilar da nuvem moderna. Não tem limite prático e garante Alta Disponibilidade (se uma máquina queimar, as outras continuam trabalhando).
- **Exemplo Prático (O clássico da Black Friday):**
  - Seu e-commerce roda com 2 servidores EC2 atrás de um Balanceador de Carga (Application Load Balancer).
  - Começa uma promoção na TV e o tráfego dispara. 
  - O **Auto Scaling Group (ASG)** detecta o uso alto de CPU e, automaticamente, sobe mais 18 servidores (Scale Out), totalizando 20 máquinas dividindo os acessos em segundos.
  - Quando a promoção acaba de madrugada, o ASG destrói 18 servidores (Scale In), voltando para 2, para que você não pague por máquinas ociosas.


# ☁️ Cloud Computing - Aula 03: Tipos de Cloud (Modelos de Serviço)

> 💡 **Foco SAA-C03:** Esses modelos definem o **Modelo de Responsabilidade Compartilhada**. Onde termina a obrigação da AWS e onde começa a sua? A resposta depende de qual modelo você está usando.

## 🏢 On-Site (On-Premises / Data Center Local)
- **O que é:** O modelo tradicional de TI, fora da nuvem. A sua empresa possui fisicamente os servidores em seu próprio prédio.
- **Sua Responsabilidade (100%):** Você gerencia **TUDO**. Desde a segurança física do prédio, ar-condicionado, cabos de rede, compra de racks, hypervisor de virtualização, até o sistema operacional, banco de dados e a aplicação final.
- **Característica:** Alto custo inicial (CapEx) e ciclos de atualização lentos.

---

## 🛠️ IaaS (Infrastructure as a Service / Infraestrutura como Serviço)
- **O que é:** Você aluga a infraestrutura básica de TI (servidores virtuais, rede e armazenamento). É o modelo de nuvem mais flexível e mais próximo da TI tradicional.
- **A AWS gerencia:** O hardware físico, a rede física, a energia, a segurança do data center e o Hypervisor (sistema de virtualização).
- **Você gerencia:** O Sistema Operacional (instalar atualizações de segurança do Linux/Windows), a configuração do banco de dados, o tráfego de rede (Security Groups) e a aplicação.
- **Exemplos clássicos na AWS:** **Amazon EC2** (Máquinas Virtuais), **Amazon EBS** (Discos) e **Amazon VPC** (Rede).

---

## 🏗️ PaaS (Platform as a Service / Plataforma como Serviço)
- **O que é:** A nuvem fornece não apenas a infraestrutura, mas também o sistema operacional e as ferramentas de banco de dados/execução prontas. Remove a necessidade de gerenciar a infraestrutura subjacente.
- **A AWS gerencia:** O hardware, o Hypervisor, **E o Sistema Operacional**, incluindo os patches de segurança e atualizações de versão.
- **Você gerencia:** Apenas o seu código (Aplicações) e os seus dados.
- **Exemplos clássicos na AWS:** **AWS Elastic Beanstalk** (Você só faz upload do código e ele provisiona tudo), **Amazon RDS** (Banco de Dados Relacional gerenciado, onde você não tem acesso ao Linux que roda por baixo) e **AWS Lambda**.
- **Benefício:** Aumenta a produtividade dos desenvolvedores, pois eles não precisam perder tempo administrando servidores.

---

## 📦 SaaS (Software as a Service / Software como Serviço)
- **O que é:** Um produto final, completo, operado e gerenciado inteiramente pelo provedor de serviços. O cliente apenas consome o serviço via internet, geralmente por um navegador.
- **A AWS/Provedor gerencia:** **TUDO**. Hardware, SO, patches, código da aplicação, escalabilidade e segurança.
- **Você gerencia:** Basicamente as suas credenciais de acesso e a configuração de uso do software.
- **Exemplos clássicos:** **Gmail**, **Dropbox**, **Salesforce**. Na AWS, serviços como **Amazon Connect** (Call center na nuvem) ou **Amazon Rekognition** (API de reconhecimento de imagem pronta para uso).

---

## 🗺️ O Modelo de Responsabilidade

A transição do On-Site para o SaaS representa a transferência de "dor de cabeça" (gerenciamento) do Cliente para o Provedor de Nuvem. No IaaS você tem controle total, mas trabalha mais. No SaaS, você não tem trabalho de infraestrutura, mas perde o controle do que roda por baixo.

![Modelo de Responsabilidade Compartilhada](assets/RESPONSIBILITY-MODEL.png)


# ☁️ Cloud Computing - Aula 04: Modelos de Implantação (Deployment Models)

> 💡 **Foco SAA-C03 (Cenário Clássico):** A prova adora explorar a **Nuvem Híbrida**. Geralmente, a questão descreve uma empresa com um banco de dados legado, dados ultrassecretos ou regras de compliance severas que *"não permitem que os dados saiam do prédio"*, mas eles querem usar a nuvem para suportar picos de acesso no site. A resposta envolverá sempre uma arquitetura Híbrida (conectando o local físico à AWS de forma segura).

## 🌍 1. Public Cloud (Nuvem Pública)
- **O que é:** Os serviços em nuvem são fornecidos por um provedor terceirizado (como a própria AWS, Azure ou Google Cloud) e disponibilizados para qualquer pessoa pela internet.
- **Características:** 
  - **Multitenancy (Múltiplos Inquilinos):** Você compartilha o mesmo hardware físico com milhares de outras empresas (embora os seus dados sejam isolados logicamente de forma segura).
  - Sem necessidade de investimento inicial em infraestrutura (Zero CapEx).
  - Escalabilidade virtualmente infinita e modelo 100% *Pay-as-you-go*.
- **Uso:** Startups, aplicações web globais, Big Data, e-commerce, empresas que nasceram digitais.

---

## 🏢 2. Private Cloud (Nuvem Privada / On-Premises)
- **O que é:** A infraestrutura de nuvem é operada exclusivamente por (e para) **uma única organização**. Pode estar localizada fisicamente no data center da própria empresa (On-Premises) ou hospedada por terceiros, mas a rede é totalmente dedicada.
- **Características:**
  - **Single-tenant (Inquilino Único):** O hardware não é compartilhado com ninguém.
  - Controle e personalização absolutos sobre a segurança, servidores e rede.
  - Custo altíssimo de manutenção (CapEx e mão de obra).
- **Uso:** Bancos, instituições governamentais, hospitais ou empresas com regras de conformidade (Compliance) extremamente rígidas que não confiam ou não têm permissão legal para colocar dados na nuvem pública.

---

## 🌉 3. Hybrid Cloud (Nuvem Híbrida)
- **O que é:** É a combinação das duas nuvens (Pública + Privada), ligadas por uma tecnologia padronizada (como *AWS Direct Connect* ou *VPN*) que permite o compartilhamento seguro de dados e aplicativos entre elas.
- **Características:**
  - Mantém o controle rígido sobre dados sensíveis (ficam na Nuvem Privada).
  - Usa a elasticidade da AWS para suportar picos de processamento (ficam na Nuvem Pública).
- **Exemplo Prático de Prova (Cloud Bursting):** 
  - Uma empresa mantém seu servidor web e banco de dados rodando em seu Data Center local (Privada).
  - Durante a Black Friday, a capacidade local esgota. O sistema é configurado para "transbordar" automaticamente o tráfego excedente para novas instâncias EC2 na AWS (Pública). 
  - Quando o evento acaba, a AWS é desligada e a empresa volta a usar apenas seu servidor local.

# ☁️ Cloud Computing - Aula 05: Os Principais Serviços AWS (Mapa SAA-C03)

> 💡 **Dica de Prova:** Você não precisa conhecer os 200+ serviços da AWS. A certificação SAA-C03 exige que você saiba categorizar e escolher o serviço certo para o problema certo. Decore as palavras-chave de cada um!

## 🖥️ 1. Computação (Compute)
Onde o processamento acontece (os "cérebros").
- **Amazon EC2:** Servidores virtuais na nuvem (IaaS). Máquinas flexíveis para qualquer uso.
- **AWS Lambda:** Computação *Serverless* (Sem servidor). Roda código apenas quando um evento acontece. Cobrado por milissegundo.
- **Amazon ECS / EKS:** Orquestração de **Contêineres** (Docker). ECS é o nativo da AWS, EKS é o Kubernetes gerenciado.
- **AWS Elastic Beanstalk:** Serviço PaaS para fazer deploy rápido de aplicações web (você foca no código, ele provisiona os servidores e balanceadores).

## 🗄️ 2. Armazenamento (Storage)
Onde os arquivos e discos vivem.
- **Amazon S3:** Armazenamento de **Objetos**. Escala infinita, backups, sites estáticos e Big Data.
- **Amazon EBS:** Armazenamento em **Blocos**. É o "disco rígido" (SSD/HDD) conectado na sua instância EC2.
- **Amazon EFS:** Sistema de **Arquivos** de rede elástico (NFS). Pode ser montado em centenas de instâncias EC2 ao mesmo tempo (apenas Linux).
- **AWS Storage Gateway:** Conecta a infraestrutura On-Premises ao S3 (Nuvem Híbrida).

## 🗃️ 3. Bancos de Dados (Databases)
- **Amazon RDS:** Bancos de dados **Relacionais** SQL gerenciados (MySQL, PostgreSQL, Oracle, SQL Server).
- **Amazon Aurora:** Banco relacional criado pela AWS. 5x mais rápido que MySQL tradicional, altamente disponível.
- **Amazon DynamoDB:** Banco de dados **NoSQL** (Chave-Valor) *Serverless*. Latência de milissegundos, não importa o tamanho.
- **Amazon ElastiCache:** Banco de dados em **Memória** (Redis ou Memcached). Usado para aliviar consultas repetitivas no banco principal (Cache).

## 🌐 4. Redes e Entrega de Conteúdo (Networking)
- **Amazon VPC:** A sua rede privada virtual na nuvem. Onde você define sub-redes, IPs e gateways.
- **Amazon Route 53:** Serviço de **DNS** altamente escalável. Faz o roteamento do seu domínio (ex: `meusite.com`) para a AWS.
- **Amazon CloudFront:** Serviço de **CDN** (Content Delivery Network). Faz cache de imagens, vídeos e APIs em pontos de presença globais (Edge Locations) para entregar rápido ao usuário final.
- **Elastic Load Balancing (ELB):** Distribui o tráfego de entrada automaticamente entre várias instâncias EC2 saudáveis.

## 🔒 5. Segurança, Identidade e Conformidade
- **AWS IAM (Identity and Access Management):** Controle de quem pode entrar na AWS (Usuários/Grupos) e o que eles podem fazer (Políticas/Roles).
- **AWS KMS (Key Management Service):** Criação e gerenciamento das **Chaves de Criptografia**.
- **AWS WAF / Shield:** WAF protege contra ataques de camada de aplicação (SQL Injection). Shield protege contra ataques **DDoS** (Negação de Serviço).

## 🔗 6. Integração de Aplicações e Mensageria
Desacopla as camadas da sua arquitetura.
- **Amazon SQS:** Serviço de **Filas** de mensagens. Um servidor manda a tarefa para a fila, o outro puxa a tarefa quando puder.
- **Amazon SNS:** Serviço de **Notificações/Publicação**. Envia alertas via E-mail, SMS ou HTTP (Pub/Sub).

## 📊 7. Gerenciamento e Governança
- **Amazon CloudWatch:** Monitoramento de **Performance**. Fica de olho no uso de CPU, memória e cria alarmes (ex: disparar o Auto Scaling se a CPU passar de 80%).
- **AWS CloudTrail:** Monitoramento de **Auditoria/API**. Registra "Quem fez o que, quando e onde" dentro da conta AWS.

# ☁️ Cloud Computing - Aula 06: Modelo de Responsabilidade Compartilhada (Shared Responsibility Model)

> 💡 **Foco SAA-C03:** A AWS ama testar esse conceito com cenários de falha de segurança. Se um hacker invadir uma instância EC2 porque a porta 22 estava aberta para o mundo, a culpa é do cliente. Se o data center físico pegar fogo ou um disco rígido físico queimar, a responsabilidade de manter a infraestrutura rodando é da AWS. 

## ⚖️ O que é o Modelo de Responsabilidade Compartilhada?
A segurança e a conformidade na nuvem não são tarefas exclusivas da AWS, mas sim uma responsabilidade dividida entre a AWS e o Cliente. 

A regra básica cobrada no exame divide a segurança em duas frases essenciais:

### 🟧 Responsabilidade da AWS: Segurança DA Nuvem (Security OF the Cloud)
A AWS é responsável por proteger e manter a infraestrutura global que executa todos os serviços oferecidos.
- **Infraestrutura Global:** Regiões (Regions), Zonas de Disponibilidade (AZs) e Pontos de Presença (Edge Locations).
- **Segurança Física:** Câmeras, seguranças armados, controle de acesso biométrico nos data centers físicos.
- **Hardware Base:** Cabeamento de rede, energia elétrica, refrigeração, troca de peças físicas.
- **Virtualização (Hypervisor):** O software de baixo nível que isola as máquinas virtuais de diferentes clientes no mesmo servidor físico.

### 🟦 Responsabilidade do Cliente: Segurança NA Nuvem (Security IN the Cloud)
O cliente é responsável por tudo o que ele implanta, coloca ou conecta dentro da nuvem.
- **Dados do Cliente (Customer Data):** Você é o único dono dos seus dados.
- **Gerenciamento de Identidade (IAM):** Criar senhas fortes, exigir MFA (Autenticação em duas etapas) e gerenciar permissões restritas de quem acessa o quê.
- **Sistemas Operacionais e Patches:** Em serviços IaaS como o **EC2**, é **VOCÊ** quem deve instalar os patches de segurança do Windows ou Linux. A AWS não toca no seu SO.
- **Configuração de Rede e Firewall:** É sua obrigação fechar ou abrir as portas corretas nos *Security Groups* e *Network ACLs*.
- **Criptografia:** Escolher ativar a encriptação dos arquivos no S3, discos EBS e dados em trânsito (HTTPS).

---

## 🔄 A Linha de Responsabilidade é Móvel
A divisão muda dependendo da categoria do serviço utilizado:
- **Serviços IaaS (Ex: Amazon EC2, EBS):** Você tem o controle total da máquina. Portanto, a responsabilidade pelo sistema operacional, patches e firewall interno da máquina é 100% sua.
- **Serviços Gerenciados / PaaS (Ex: Amazon RDS, S3, DynamoDB):** A AWS sobe a linha de responsabilidade. Ela assume a atualização do Sistema Operacional, a aplicação de patches do banco de dados e a infraestrutura de rede inferior. A sua responsabilidade fica focada apenas nos dados, na criptografia e nas permissões (IAM).

---

## 🔗 Referência Oficial
- **Documentação AWS:** [Modelo de Responsabilidade Compartilhada da AWS](https://aws.amazon.com/pt/compliance/shared-responsibility-model/)


# 💸 Amazon CloudWatch - Aula 07: Alertas de Faturamento (Billing Alarms)

> 💡 **Foco SAA-C03:** Embora o **AWS Budgets** seja a ferramenta moderna e proativa, a AWS ainda cobra os **CloudWatch Billing Alarms**. A principal diferença para a prova é: O *AWS Budgets* pode prever custos futuros, enquanto o *CloudWatch Billing Alarm* reage aos custos estimados já contabilizados.

## ⚙️ 1. O Pré-requisito (Pegadinha de Prova)
Antes de criar qualquer alarme no CloudWatch, você precisa avisar a AWS que deseja expor seus dados financeiros para ele.
- 🧭 **Caminho no Console:** `Conta (Canto superior direito) > Billing and Cost Management > Billing Preferences`
- **Ação Obrigatória:** Você DEVE marcar a caixa **"Receive Billing Alerts"** (Receber alertas de faturamento). Se não fizer isso, a métrica de dinheiro não vai aparecer no CloudWatch de jeito nenhum.

---

## 🔔 2. Como criar o Alerta (Passo a Passo)
Os alertas de faturamento são criados dentro do serviço **Amazon CloudWatch**.
- 🧭 **Caminho no Console:** `CloudWatch > Alarms > Billing > Create alarm`
- > 🚨 **Dica Crítica (Região):** Os dados de faturamento da AWS são globais, mas ficam hospedados em uma região específica. Para ver ou criar métricas de faturamento no CloudWatch, **você TEM que alterar a sua região no console para N. Virginia (us-east-1)**.

### Configurações Possíveis (O que definir no Alarme)

1. **Métrica e Condições (Thresholds):**
   - **Métrica:** `EstimatedCharges` (Encargos estimados).
   - **Moeda:** Sempre em USD (Dólares).
   - **Condição (Statistic):** Máximo (Maximum) a cada 6 horas (padrão de atualização da AWS).
   - **Threshold type (Tipo de Limite):** Você escolhe "Estático" (*Static*) e define o operador. *Exemplo:* "Disparar alarme quando o custo for **Maior que (>)** ou **Maior/Igual a (>=)** 10 dólares".

2. **Ações (Actions / Notificações):**
   - O que o CloudWatch deve fazer quando o alarme mudar para o estado `ALARM`?
   - **Integração com SNS (Simple Notification Service):** Você deve criar ou selecionar um **Tópico SNS**.
   - **Endereço:** Você insere o seu e-mail.
   - *Nota prática:* A AWS enviará um e-mail de confirmação ("Subscription Confirmation"). Se você não clicar no link de confirmação que chegar no seu e-mail, o alerta **não** vai funcionar.

3. **Granularidade (Avançado):**
   - O alarme padrão mede o *Total Estimated Charge* (Custo Total da Conta).
   - Porém, você pode criar alarmes granulares. *Exemplo:* Um alarme de US$ 5,00 exclusivo para os gastos do serviço "Amazon EC2" e outro de US$ 2,00 para "Amazon S3".


# 💻 Ferramentas de Gerenciamento - Aula 08: AWS CLI e CloudShell

> 💡 **Foco SAA-C03:** Você precisa entender as três formas principais de interagir com a AWS: O **Console Web** (Interface gráfica padrão), a **AWS CLI** (Linha de comando/Scripts) e os **SDKs** (Kits de desenvolvimento para interagir via código fonte em Java, Python, etc).

## ⌨️ 1. AWS CLI (Command Line Interface)
- **O que é:** Uma ferramenta unificada para gerenciar todos os serviços da AWS usando comandos de texto no terminal da sua máquina (Linux, macOS, Windows).
- **Vantagem Principal:** **Automação e Repetibilidade**. Permite criar scripts para automatizar tarefas diárias (ex: um script que sobe 10 instâncias EC2 e configura um Load Balancer em poucos segundos).
- **Como Autenticar (Dica de Prova):**
  - Para usar o CLI localmente, execute o comando `aws configure`.
  - Ele pedirá sua **Access Key ID**, **Secret Access Key**, **Região Padrão** (ex: `us-east-1`) e **Formato de Saída** (ex: `json`).
  - 🚨 *Segurança:* O exame tentará te induzir ao erro sugerindo colocar essas chaves escritas em texto puro dentro do código. A resposta correta é SEMPRE usar Roles (Funções IAM) nas instâncias ou o arquivo local de credenciais. Nunca deixe chaves expostas (hardcoded).

---

## ☁️ 2. AWS CloudShell
- **O que é:** Terminal de linha de comando que roda **direto no navegador**, embutido no painel web da AWS. 
- 🧭 **Caminho no Console:** Canto superior direito da tela, no ícone de terminal `>_`.

### 🌟 Por que usar o CloudShell? (Certeza de Prova)
1. **Ambiente Pronto:** Já vem com AWS CLI, Python, Node.js, Bash e PowerShell instalados.
2. **Pré-Autenticado:** Você não precisa rodar `aws configure`. O terminal já entra logado com as suas permissões do console web.
3. **Armazenamento Persistente:** A AWS te dá **1 GB de armazenamento gratuito e persistente** por região no diretório `$HOME`. Arquivos e scripts salvos ali não somem quando você fecha o navegador.

---

## 🛠️ 3. Comandos Úteis (Cheat Sheet Básico)
A sintaxe padrão de qualquer comando na AWS CLI é sempre: `aws <nome-do-serviço> <ação> [parâmetros]`

### ⚙️ Configuração e Ajuda
- `aws configure` → Inicia o assistente para configurar suas credenciais e região padrão.
- `aws <serviço> help` → Mostra o manual de como usar a CLI para um serviço específico (ex: `aws ec2 help`).

### 🪣 Amazon S3
- `aws s3 ls` → Lista todos os seus buckets.
- `aws s3 mb s3://meu-novo-bucket` → Cria um novo bucket (*Make Bucket*).
- `aws s3 cp arquivo.txt s3://meu-bucket/` → Copia um arquivo do seu computador para o S3.
- `aws s3 sync pasta-local/ s3://meu-bucket/` → Sincroniza uma pasta inteira do PC com o S3 (ótimo para subir sites estáticos).

### 💻 Amazon EC2
- `aws ec2 describe-instances` → Lista os detalhes de todas as suas instâncias EC2 (estado, IP, tipo).
- `aws ec2 start-instances --instance-ids i-1234567890abcdef0` → Liga uma instância específica.
- `aws ec2 stop-instances --instance-ids i-1234567890abcdef0` → Desliga uma instância específica.

### 🔐 AWS IAM
- `aws iam list-users` → Lista todos os usuários criados na sua conta.
- `aws iam create-user --user-name Ranon` → Cria um novo usuário no IAM.


