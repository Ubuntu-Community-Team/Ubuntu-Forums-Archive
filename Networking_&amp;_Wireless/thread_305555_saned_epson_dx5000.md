---
title: "saned epson dx5000"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by Fenix-TX on 2006-11-23
Hi! I'm trying to get working my epson Dx5000 through my network, printer works fine, and i have problems with saned. I've seen a lot of posts and documents but i can't get work it.

I've stopped xinetd to use saned -d and when i try to connect on the remote client, it shows this on server:

```
[saned] main: starting debug mode (level 2)
[saned] main: [1] bind failed: Address already in use
[saned] saned (AF-indep+IPv6) from sane-backends 1.0.18 ready
[saned] check_host: access by remote host: ::ffff:192.168.123.101
[saned] check_host: getaddrinfo failed: Name or service not known
[saned] init: access by host ::ffff:192.168.123.101 denied
[saned] quit: exiting

```

Any ideas?

---

### Post by utrescu on 2007-05-05
This is a typical error when your hostname is not in /etc/hosts. 

Look at /etc/hostname and put the name in /etc/hosts

$ cat /etc/hostname
PEPET.acme.com

And edit /etc/hosts and put it in the correct line

$ gedit /etc/hosts
127.0.0.1 localhost
127.0.1.1 PEPET.acme.com PEPET
192.168.0.2 PEPET.acme.com PEPET

---

