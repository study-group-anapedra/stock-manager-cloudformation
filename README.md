## 🏗️ Arquitetura da Aplicação (AWS)

A arquitetura do **Beer Brewery Stock Manager** foi projetada seguindo o padrão de **Três Camadas (3-Tier Architecture)**, com foco em **alta disponibilidade**, **escalabilidade**, **segurança** e **boas práticas em nuvem**.

A aplicação está distribuída em **múltiplas Availability Zones**, garantindo tolerância a falhas e continuidade do serviço.

### 📌 Visão Geral da Arquitetura

O fluxo de acesso à aplicação ocorre da seguinte forma:

1. O usuário acessa a aplicação via navegador (Web Client)
2. O domínio é resolvido pelo **Amazon Route 53**
3. O conteúdo é distribuído pelo **Amazon CloudFront (CDN)**
4. As requisições passam por uma camada de proteção com **AWS WAF**
5. O tráfego é direcionado para um **Application Load Balancer (ALB)**
6. O ALB distribui as requisições entre **instâncias EC2**, organizadas em **Auto Scaling Groups**
7. A aplicação acessa o banco de dados **Amazon RDS (PostgreSQL)** em configuração **Multi-AZ**
8. Serviços auxiliares como **Amazon ElastiCache (Redis)** e **Amazon EFS** são utilizados para cache e armazenamento compartilhado
9. O acesso à internet a partir de subnets privadas é realizado por meio de **NAT Gateways**

Essa arquitetura garante:
- Balanceamento de carga automático
- Escalabilidade horizontal
- Isolamento de rede com subnets públicas e privadas
- Alta disponibilidade do banco de dados
- Camadas adicionais de segurança na borda e na aplicação

### 🖼️ Diagrama da Arquitetura

O diagrama abaixo representa visualmente a arquitetura utilizada no projeto:

🔗 **Diagrama de Arquitetura AWS**  
https://github.com/study-group-anapedra/brewery-stock-manager/blob/develop/docs/adicionar-diagrama-aws-arquitetura.png
