# Sistemas Operativos (SO)

![IST](img/IST_DEI.png)  

## Definição do ambiente laboratorial

O ambiente onde são testados os exercícios, em caso de dúvidas, são os sistemas Linux nos laboratórios das aulas.

- [Rede das Novas Licenciaturas - Alameda](https://rnl.tecnico.ulisboa.pt/laboratorios/software/)
- [Núcleo de Informática do Taguspark](http://groups.tecnico.ulisboa.pt/lti-tagus/software/)

Dito isto, os sistemas Linux, em geral, deverão executar corretamente os exercícios e permitir o desenvolvimento do projeto.
No entanto, é **fortemente recomendado** que o **código**, sobretudo do **projeto**, seja **testado regularmente no ambiente de referência**.

### Acesso remoto ao ambiente de referência

Os computadores dos labs da Alameda podem ser acedidos de forma remota com SSH (*Secure Shell*), no entanto, não diretamente: é preciso antes aceder a uma máquina com acesso aos PCs dos labs.

Para este efeito pode-se usar o [*cluster* da RNL](https://rnl.tecnico.ulisboa.pt/servicos/cluster/).
A autenticação é feita com o IST ID e palavra-passe do Fénix. 
<!--
A *home* de cada utilizador (directoria presente quando se faz *login*) consiste na sua área pessoal do AFS disponibilizada pela DSI.
É necessário, portanto, que o serviço AFS esteja ativo no [selfservice da DSI](https://selfservice.dsi.tecnico.ulisboa.pt/).
-->

```bash
ssh ist1XXXXXX@cluster.rnl.tecnico.ulisboa.pt
```

Depois de entrar na *shell* do *cluster*, é possível aceder aos computadores dos labs por SSH. 
O computador precisa de estar ligado e a executar o sistema Linux. 
O seguinte comando lista os computadores neste estado:

```bash
# Correr no cluster
sinfo -Nr
```

Qualquer um dos computadores listados pode ser usado:

```bash
# Correr no cluster após substituir X e Y
ssh labXpY
```

----

## Ambientes alternativos

Feita a ressalva anterior de **testar sempre no ambiente de referência**, listamos de seguida alguns ambientes que também têm sido usados para o desenvolvimento de código no âmbito de SO.

**O único ambiente que será oficialmente suportado é o ambiente de referência.**  
Em todo os outros ambientes, o utilizador está por conta própria.

Os docentes tentarão sempre ajudar a resolver problemas, mas não têm obrigação de o fazer, por limitações de tempo e esforço.

### *Windows Subsystem for Linux* (WSL)

O subsistema de Linux para Windows (*Windows Subsystem for Linux* -- WSL) permite correr um Linux dentro do Windows de forma mais eficiente do que usando uma máquina virtual.
Facilita também a partilha de ficheiros entre o Windows e o Linux.

Sugere-se a consulta de uma [explicação do WSL](https://learn.microsoft.com/en-us/windows/wsl/about) e das [instruções para a instalação](https://learn.microsoft.com/en-us/windows/wsl/install).
Existem também [instruções focadas no Ubuntu](https://www.omgubuntu.co.uk/how-to-install-wsl2-on-windows-10).

### macOS

O macOS é também um sistema Unix, mas não é um sistema Linux.
Existem diferenças importantes na estrutura interna do sistema e no licenciamento.  
**Importante:** a nível da programação de sistema, poderão surgir algumas diferenças, por exemplo, na gestão dos *signals*.
Tentaremos confirmar estas incompatibilidades ao longo do período de aulas.  
**Relembramos a necessidade de testar regularmente no ambiente de referência: o Linux dos laboratórios.**

Para permitir o desenvolvimento será necessário instalar as ferramentas que são incluidas no [XCode](https://developer.apple.com/xcode/).  
Pode também ser útil ter o [Homebrew](https://www.makeuseof.com/tag/install-mac-software-terminal-homebrew/) para instalar mais ferramentas, se necessário.

### Acesso remoto ao Sigma

O Técnico disponibiliza um serviço de [*Unix shell*](https://si.tecnico.ulisboa.pt/en/servicos/servidores-e-dados/unix-shell/), que é suportados pelas [máquinas Sigma](https://si.tecnico.ulisboa.pt/en/servicos/servidores-e-dados/unix-shell/acesso-ao-cluster-sigma/) que podem ser usadas remotamente com SSH.

### *Dual Boot*

Na maior parte das máquinas, é possível instalar mais do que um SO e depois escolher qual corre no arranque do sistema.
Cada sistema terá de ter uma ou mais partições de disco próprias.

**Atenção:** este tipo de configuração pode, em caso de engano, estragar toda a instalação da máquina e obrigar a uma reinstalação total, com perda de todos os ficheiros contidos no computador, num processo que demora várias horas.  
Avançar apenas com uma cópia de salvaguarda (*backup*) integral de todos os ficheiros e com acesso a meios de reinstalação do sistema operativo original, caso venham a ser necessários.

### *Boot from USB*

Neste caso, é escolhida uma memória USB, onde é instalada uma imagem do sistema operativo Linux.
É importante que seja escolhida uma opção onde é possível guardar ficheiros na imagem, de modo a não perder o trabalho realizado.

Ao iniciar a máquina, deve ser possível escolher a opção de arrancar a partir do USB.
Em muitos casos, é necessário configurar o arranque do computador para escolher arrancar no dispositivo USB em primeiro lugar.
Será necessário procurar instruções para aceder à UEFI ou BIOS no seu modelo de computador e depois fazer a configuração.

A memória USB deverá oferecer tempos de acesso rápidos, em especial no tempo de escrita, para que o desempenho seja bom.
Tenha em atenção que a memória USB a usar irá sofrer um grande desgaste de escritas, pelo que verá o seu tempo de vida substancialmente encurtado.

### Máquina virtual

Uma máquina virtual é um computador que é simulado por outro computador.
Na virtualização existem três entidades principais: o anfitrião (*host*) que é o sistema de base; o convidado (*guest*) que é o sistema virtual; e o monitor de máquina virtual, também chamado hipervisor (*hypervisor*), que é quem faz de intermediário entre o anfitrião e o convidado.

O [VirtualBox](https://www.virtualbox.org/) é um hipervisor gratuito, disponível para os sistemas operativos mais usados.
No entanto, existem limitações de compatibilidade entre arquiteturas de processador: a arquitetura da máquina virtual (por exemplo, [x86-64](https://en.wikipedia.org/wiki/X86-64)) deve ser compatível com a arquitetura do anfitrião.
Consulte as [tabelas de compatibilidade na documentação](https://docs.oracle.com/en/virtualization/virtualbox/7.2/user/Introduction.html).

**Nota:** O uso de máquina virtual é recomendado apenas para quem tiver uma máquina com mais de 2 *cores*, mais de 4GB de RAM e mais de 40GB de disco livre no computador.

Se decidir avançar, deve [obter e instalar o VirtualBox na máquina](https://www.virtualbox.org/wiki/Downloads).
Após a instalação, é recomendado instalar também o pacote de extensões (*extension pack*) para suporte avançado de dispositivos USB e partilha de pastas.

Será ainda necessário instalar o Linux numa máquina virtual a criar com o VirtualBox.

A qualquer momento, com a máquina virtual parada ou em execução, é possível tirar um *snapshot* (retrato) ao estado da máquina, que pode depois ser recuperado.
Recomenda-se que os retratos sejam tirados com a máquina virtual desligada, por ser uma situação mais estável e por não implicar o armazenamento do estado da memória RAM.
Em todo o caso, os retratos são armazenados e ocupam espaço em disco, sendo guardadas apenas as diferenças.
O uso de *snapshots* permite, de uma forma eficaz e conveniente, fazer experiências no sistema operativo da máquina virtual e recuperar um estado anterior, se necessário.

----

Contactos para sugestões/correções: [LEIC-Alameda](mailto:leic-so-alameda@disciplinas.tecnico.ulisboa.pt), [LEIC-Tagus](mailto:leic-so-tagus@disciplinas.tecnico.ulisboa.pt), [LETI](mailto:leti-so-tagus@disciplinas.tecnico.ulisboa.pt)
