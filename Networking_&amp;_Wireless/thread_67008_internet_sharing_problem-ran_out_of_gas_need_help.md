---
title: "internet sharing problem-ran out of gas need help"
date: 2005-09-19
forum: Networking &amp; Wireless
---

### Post by tuna3000 on 2005-09-19
hi, im just 1 week old linux user

i have managed to install/config my clients networking,
now im working on my ubuntu linux server (previously a win2k3 server with kerio winroute), managed to config internet connection (using 'gasp' speedtouch usb modem), problem- I CANT SHARE MY INTERNET CONNECTION! i tried Firestarter but it didnt shared, well it firewalled, i'm exhausted a bit, can someone help me (note what my previous server is, a point and click-cant learn new things-OS). linux pumped my blood, now the fun in computing is coming back to me, thanks

---

### Post by s_p_a_r_k_y on 2005-09-19
type this
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
if your external network device is eth0, otherwise replace it.
And make sure that
/proc/sys/net/ipv4/ip_forward
has a 1 in it.

Now try accessing the net from a client.

---

### Post by tuna3000 on 2005-09-20
still wont browse

server ubuntu/speedtouch(ppp0)/LAN(eth0 10.0.0.1)
hub
client ubuntu/LAN(eth0 10.0.0.x)(dns-10.0.0.1)(default gateway 10.0.0.1) <-is this correct?

tried firestarter - failed
tried fwbuilder - failed and cost me a re-installation

---

### Post by tuna3000 on 2005-09-23
got it

miracles happen

got rc.firewall - and it just boom! worked

---

### Post by fordfan753 on 2005-09-23
[QUOTE=tuna3000]got it

miracles happen

got rc.firewall - and it just boom! worked[/QUOTE]

Nice! I would have just given up and got an ethernet modem and used a switch to share the connection that way.

---

