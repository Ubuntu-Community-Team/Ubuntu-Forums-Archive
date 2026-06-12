---
title: "Weird command expansion of iptables command."
date: 2016-07-07
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2016-07-07
ON Ubuntu 14,04 LTS I am attempting to close port 11 to the outside world. I have found a lot of information on doing this but I can't get any of the commands to actually work.

One command line I found was this 

iptables -A INPUT -p tcp !-s 192.168.1.0/24 --dport 111 -j DROP; iptables -A INPUT -p tcp -s 127.0.0.1 --dport 111 -j ACCEPT

However when I run the line below in a root bash shell (sudo bash)

iptables -A INPUT -p tcp !-s 192.168.1.0/24 --dport 111 -j DROP

I get this:

iptables -A INPUT -p tcp sudo  iptables -A INPUT -p tcp sudo bash 192.168.1.0/24 --dport 111 -j DROP iptables -A INPUT -p tcp -s 127.0.0.1 --dport 111 -j ACCEPT  192.168.1.0/24 --dport 111 -j DROP
Bad argument `sudo'
Try `iptables -h' or 'iptables --help' for more information.

What am I doing wrong.

---

### Post by steeldriver on 2016-07-07
! has a special meaning in the interactive bash shell - it introduces a history expansion. You need some whitespace between the ! and the -s to stop that happening

```

iptables -A INPUT -p tcp ! -s 192.168.1.0/24 --dport 111 -j DROP

```

---

### Post by rsteinmetz70112 on 2016-07-07
Thanks that solved it.

I would have sworn I tried that but I guess I didn't

---

