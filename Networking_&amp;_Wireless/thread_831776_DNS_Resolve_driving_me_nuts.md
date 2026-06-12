---
title: "DNS Resolve driving me nuts"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by Nortonw on 2008-06-17
Hi All

I am running Sever 8.04 with KDE desktop.
I am picking up DHCP address with no problems and also dns server IPs.
The problem I have is that I cannot resolve a single hostname when I ping??
When I ping xyz.xyz I get an Unknown host msg. If I ping the IP address I have no problems.
What I find crazy is that if I use Dig xyz.xyz it resolves with no issue !!!!!!!!
I have been trying to fix this for hours and its driving me nuts.
I cant resolve my proxy server name so I cant get out to web to get updates etc.
I am on my windows box to post this.
Please Help !!!!!!

Why does dig work but not ping ??

---

### Post by superprash2003 on 2008-06-17
please post the output of cat /etc/resolv.conf from the terminal

---

### Post by Nortonw on 2008-06-17
The output is :-

nameserver 127.0.0.1
nameserver xx.xx.xx.xx
nameserver xx.xx.xx.xx

xx.xx.xx.xx = my dns servers and is right.

The 127.0.0.1 is there because I have installed dnsmasq in a bid to try and help me resolve stuff but it hasnt made a difference.

Even without this it dosent work.

Dig works first time as does nslookup but ping does not.

---

### Post by Nortonw on 2008-06-17
I have managed to get APT to work now by manually setting the information in the apt.conf file but I still cant ping resolve anything.

---

### Post by superprash2003 on 2008-06-17
your dns server is pointing to your own pc's ip.. thats the problem.. follow this tutorial to setup dns servers [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html) .. opendns is used in this example you can change it to whatever you like

---

