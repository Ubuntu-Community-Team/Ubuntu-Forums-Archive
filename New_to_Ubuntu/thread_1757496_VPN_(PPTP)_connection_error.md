---
title: "VPN (PPTP) connection error"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by anohs on 2011-05-13
I am trying to connect to my school VPN using PPTP. I used graphical interface (found on right hand side on the screen) to create a connection.

But I am getting error 'VPN Connection failed'. I am using the same connection from Windows 7, and its working fine.

I got some additional information to configure VPN without using graphical interface. For that, i need to create a file in /etc/ppp/peers. How can I do that??

---

### Post by anohs on 2011-05-13
I somehow managed to find a document, which mentions how to configure VPN. But i suppose its too old. 

I created a connection called Toto. If i  execute "pon Toto debug nodetach" i am getting following error



```

Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
anon warn[pptp_gre_bind:pptp_gre.c:87]: socket: Operation not permitted
anon fatal[main:pptp.c:322]: Cannot bind GRE socket, aborting.
Modem hangup


```

---

