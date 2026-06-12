---
title: "Configuring networkmanager to use my DNS"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by rohandhruva on 2007-02-21
Hi,

I have eth0 as my wired connection. It uses DHCP. Networkmanager configures it fine, but it uses some default DNS which doesnt work. I want to have it use a dns I specify - can someone please help me do that ? Also, is there some distro-agnostic way about it, so that I can use the same method for other distros ?

Thanks !

---

### Post by dtf on 2007-02-21
I believe your dns computers are specified in /etc/resolv.config like below.  I think that dhcp sets this up for you but it is possible to add your own dns server.

Example of my /etc/resolv.conf.  In this example the first one does not really work.  It getsthis from my linksys router which I configured with dhcp but specifed the invalid address which I never bothered to clean up.  Otherwise it works fine.

nameserver 192.168.1.1
nameserver 206.141.192.60
nameserver 206.141.193.55

---

