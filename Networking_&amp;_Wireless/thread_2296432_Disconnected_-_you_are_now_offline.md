---
title: "Disconnected - you are now offline"
date: 2015-09-25
forum: Networking &amp; Wireless
---

### Post by ropieur2 on 2015-09-25
Hi,

The network connection suddenly stops working.
Xubuntu 14.04 displays "Disconnected -  you are now offline" when I enter my session.

My PC dual boots Ubuntu 12.04 and Xubuntu 14.04 (hardware being not well supported with compiz, I am running xubuntu 14.04 instead of ubuntu)
Ubuntu 12.04 connects correctly to the network and internet. So this excludes cable issue, router issue and PC hardware issue.

As there is no connection at all, it is even difficult for me to copy/paste result of commands.

I already tried to edit /etc/network/interfaces and add 
```
auto eth0
iface eth0 inet dhcp
```

followed by:
```
sudo service network-manager restart
sudo ifconfig eth0 up
```

But the problem persists.

Can someone help me how I can investigate and solve this issue ?

Is there any possibility to force at least temporary network connection in order to simplify reporting here? If yes how?

Thanx in advance

---

### Post by ropieur2 on 2015-09-26
I managed to configure networking by hand.
I can connect local network and by editing /etc/resolv.conf (adding nameserver 8.8.8.8), internet is accessible.

---

### Post by ropieur2 on 2015-09-26
reinstalling resolvconf did not help

---

