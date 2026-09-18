#  Laboratório de Infraestrutura Segura e Hardening de Redes

##  Sobre o Projeto
Este projeto consiste na criação, configuração e proteção de um servidor Linux do zero, fundamentado em boas práticas de cibersegurança, isolamento de rede e administração remota. O ambiente foi desenhado para atuar como a base de um laboratório corporativo simulado, focado em testes defensivos e arquitetura de redes.

##  Ferramentas Utilizadas
- **Sistema Operacional:** Ubuntu Server 24.04 LTS
- **Virtualização:** Oracle VirtualBox 7.2
- **Configuração de Rede:** Netplan (YAML)
- **Segurança e Acesso:** UFW (Uncomplicated Firewall), OpenSSH

##  Arquitetura e Implementações Técnicas
1. **Administração Remota Criptografada (SSH):** 
   - Estabelecimento de acesso via linha de comando do *host* para a máquina virtual utilizando *port forwarding* (direcionamento de portas), simulando o acesso a um servidor em *datacenter*.
2. **Segmentação de Rede Dupla:**
   - **`enp0s3` (Interface Pública/NAT):** Fornece conectividade de internet controlada para baixar pacotes e atualizações de segurança.
   - **`enp0s8` (Interface Privada/Rede Interna):** Rede isolada (`LAB-SEC`) operando no bloco IP `192.168.10.0/24` para comunicação exclusiva, invisível para redes externas.
3. **Hardening de Firewall (UFW):**
   - Implementação do princípio do menor privilégio na rede.
   - Regra `default deny incoming` para bloquear varreduras de portas e ataques externos.
   - Liberação exclusiva para tráfego gerencial (Porta 22/TCP).
