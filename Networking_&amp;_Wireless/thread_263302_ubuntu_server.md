---
title: "ubuntu server"
date: 2006-09-22
forum: Networking &amp; Wireless
---

### Post by patz on 2006-09-22
anybody help me to install ubuntu server? I setup ubuntu 6.06 version and I want to share the connection of internet but i wasn't able to connect i had two ethernet card installed 1 for the static IP and 1 for the dynamic IP wich is for the client. My static IP is ok because i was able to connect to internet my prolem is i'm trying to connect the client but wasn't work. anybody help me?

---

### Post by fstab on 2006-09-23
Did you enable IP Forwarding?

sh-3.1$ cat /proc/sys/net/ipv4/ip_forward
0

It's gotta be set to 1 to forward packets.

---

