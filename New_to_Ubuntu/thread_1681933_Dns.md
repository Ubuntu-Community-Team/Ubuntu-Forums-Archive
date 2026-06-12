---
title: "Dns"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by pmohankumar on 2011-02-05
In a LAN, iam having both windows and linux systems. I always use system name to connect two windows systems through VNC and RUN. I can't connect the linux systems by system name from windows. i frquently using IP address to connect windows and linux system. I already installed SAMBA in linux system. By using IP i could connect linux and windows system. since i can't remember all IP address, If it's a system name, it will be better. Kindly reply the solution.........

Iam using UBUNTU 9.10 and XP[-X

---

### Post by HermanAB on 2011-02-05
Howdy,

Since you only have two machines, but the names and IP addresses in /etc/hosts and c:\windows\system32\etc\hosts

The machine will look in hosts first, before sending out a DNS query.

---

