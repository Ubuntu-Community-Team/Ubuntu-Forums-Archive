---
title: "Ubuntu_server_artica_networking_problem"
date: 2013-11-29
forum: Networking &amp; Wireless
---

### Post by iuri.f.aires on 2013-11-29
Boas, 
tenho um problema, tenho windows server 2008R2 com active directory, windows server 2012R2 com DHCP, tudo configurado e a funcionar, tenho ubuntu server para usar como servidor proxy e servidor de mail, uso o artica para instalar squid(proxy), postfix e mail server. O problema que me acontece é que o servidor ubuntu quando se lembra dá me um problema que só consegui resolver uma vez.
Está por DHCP, entao o meu problema é ficar sem ligação a internet, fui verificar o ip nas interfaces, passei de dhcp para estatico quando me apercebi que quando tentava fazer stop e start o ubuntu me apresentava este erro"/usr/lib/avahi/avahi-daemon-check-dns.sh: 1: /etc/default/avahi-daemon: AVAHI_DAEMON_START: not found".
entao entrei no ficheiro /etc/default/avahi-daemon com o nano para ver as configurações que me apareciam, pois procurei na net por tal erro e nao encontrei nada.
"AVAHI_DAEMON_START = 0
AVAHI_DAEMON_DETECT_LOCAL=1"
Então passei o valo do "AVAHI_DAEMON_START " para 1, tentei voltar fazer restart ao serviço networking, quando me apercebi que não existia tal ficheiro, o ubuntu com este erro tira as permições ao ficheiro /etc/init.d/networking e muda-lhe o nome para /etc/init.d/networking.back, então mudei-lhe o nome para o original e dei-lhe permições com o o comando "chmod 777 /etc/init.d/networking". a seguir a fazer isto consegui que o ubuntu fizesse restart a networking recebe-se o ip que lhe estava a dar e consegui ter net.
Então depois de mais umas configurações e instalações de serviços no ubuntu voltou a dar o mesmo erro, mas desta vez mesmo fazendo o anterior nao consegui com que o ubuntu recebe-se o Ip que lhe dei, mesmo reiniciando o ubuntu o ip nem por nada se muda e continua a dar o erro de antes.
entao como tinha snapshot's de configurações quando o ubuntu funcionava como deve ser tentei aplicar 3 das minhas snapshot's, mas o erro nao sei como que nao existia nessas snapshot's foi passado para lá, estou a usar o Hiper-v para as maquinas virtuais, não percebi pois as snapshot's deveriam ser completamente isentas a incrementações, principalmente de erros.
Bem Procurei mais um pouco e não encontrei solução, vou recomeçar com uma maquina nova e deixo aqui o erro. :D
Abraço e boa continuação a todos.
P.s - se alguem me souber dizer algo sobre o erro, força. :D

---

