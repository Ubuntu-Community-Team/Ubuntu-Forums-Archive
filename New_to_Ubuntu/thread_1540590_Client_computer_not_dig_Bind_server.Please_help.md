---
title: "Client computer not dig Bind server.Please help"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by honey_bee on 2010-07-28
I have configureed Bind in a Linux box. Well Well **pc1 i.e "pc1.mydomain.com" is my client machine **and main server is the computer in which bind is install.The client computer pc1 and the main server (Bind server) i.e FQDN "mainserver.mydomain.com "are on the same network.from client machine i can't resolve the name to IP address as my server do successfully with client.
The /etc/resolv.conf file in my bind server is as


Code:
search mydomain.comnameserver 192.168.1.254
At my client computer when I use dig command

Code:
[root@pc1 root]# dig A mainserver.mydomain.com
it does't resolve [IMG]http://c0491962.cdn.cloudfiles.rackspacecloud.com/images/questions/images/smilies/confused.gif[/IMG]

Kindly help me .....please

thanks
honey

---

