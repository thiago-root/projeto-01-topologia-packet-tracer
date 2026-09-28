# Projeto 1: Infraestrutura de Rede Corporativa e Troubleshooting de Serviços (Cisco Packet Tracer)

## 📌 Visão Geral do Projeto
Este projeto consiste na implementação, validação e solução de problemas (*troubleshooting*) de uma infraestrutura de rede local corporativa utilizando o Cisco Packet Tracer. 

O ambiente conta com distribuição automática de endereçamento IP (DHCP), resolução de nomes interna (DNS) e hospedagem de aplicação web corporativa (HTTP).

---

## 📐 Estrutura da Topologia
- **Roteador Central:** `192.168.1.1/24` (Default Gateway)
- **Servidor Corporativo Unificado:** `192.168.1.2/24` (Serviços DHCP, DNS e Web)
- **Escopo DHCP (Clientes):** `192.168.1.10` a `192.168.1.50`
- **Arquivo de Topologia:** O arquivo de simulação `infraestrutura_rede_corporativa.pkt` está disponível na raiz deste repositório para download e validação prática.

---

## 🧪 Serviços Configurados
1. **DHCP Server:** Distribuição automática de IP, Máscara, Gateway e Servidor DNS para os computadores clientes.
2. **DNS Server:** Mapeamento do nome de domínio FQDN `empresa.local` para o IP `192.168.1.2`.
3. **HTTP Server:** Hospedagem da página da Intranet Corporativa.

---

## 🔍 Estudo de Caso: Troubleshooting de Falha de DNS em Ambiente Corporativo

### 1. Cenário e Descrição do Incidente
Um usuário da estação de trabalho `PC-Vendas-01` abriu um chamado informando que não conseguia acessar o portal da Intranet Corporativa através do endereço web corporativo (`http://empresa.local`).

---

### 2. Análise e Diagnóstico Técnico (Passo a Passo)

#### Passo A: Reprodução do Sintoma
Acessou-se o navegador da estação de trabalho e tentou-se a navegação até a URL `http://empresa.local`. O navegador retornou o erro **"Host Name Unresolved"**, indicando falha na resolução do nome de domínio.

![Erro de Navegação - Host Name Unresolved](./01_sintoma_browser_falha.png)

#### Passo B: Isolamento de Camada (Camada 3 vs. Resolução de Nomes)
Para descartar problemas físicos de cabeamento, porta de switch ou endereçamento IP (Camada 3), executou-se um teste ICMP (*ping*) diretamente para o IP do servidor web corporativo:

```cmd
ping 192.168.1.2
