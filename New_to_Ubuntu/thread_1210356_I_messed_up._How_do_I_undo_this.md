---
title: "I messed up. How do I undo this?"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by mvalviar on 2009-07-11
```
1. Start by configuring the network card that interfaces to the other computers on you network:

# ifconfig ethX ip

where ethX is the network card and ip is your desired server ip address (Usually 192.168.0.1 is used)

2. Then configure the NAT as follows:

# iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE

where ethX is the network card that the Internet is coming from

# echo 1 > /proc/sys/net/ipv4/ip_forward

```

I issued the preceding commands as root (it's a mistake I learn from for sure). I issued ```
#ifconfig eth0 192.168.0.1
``` which I undid with```
ifconfig eth0 192.168.0.101
```. I issued ```
#iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```. How do I undo this?

---

### Post by LewRockwell on 2009-07-11
after hacking around in root and running into problems...one is indeed wise to enjoy the re-install with the confidence and knowledge gained from such adventures...

to remain in one's cocoon is to never fly...

.

---

### Post by NESFreak on 2009-07-11
iptables-restore

---

### Post by superprash2003 on 2009-07-11
you could just flush your iptables [http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html](http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html)

---

