---
title: "How can I use 2 internet connections on one computer"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by albox on 2008-02-04
Hi,
I have 2 internet connections at home : a wireless and a cable connection.
I'd like to use both connections on my laptop. ifconfig shows the 2 ip addresses. Now, I would like to know if I can set up a process (firefox for example) to use one connection and another process (a web server) to use the other connection ?
Should I use iptables ?
There is an option called --pid-owner but the ubuntu manual says that this option is not working by default (the kernel has to recompiled to activate an option...).
Is there any other solution ?

Thanks

---

### Post by roaldz on 2008-02-04
> **albox said:**
> Hi,
I have 2 internet connections at home : a wireless and a cable connection.
I'd like to use both connections on my laptop. ifconfig shows the 2 ip addresses. Now, I would like to know if I can set up a process (firefox for example) to use one connection and another process (a web server) to use the other connection ?
Should I use iptables ?
There is an option called --pid-owner but the ubuntu manual says that this option is not working by default (the kernel has to recompiled to activate an option...).
Is there any other solution ?

Thanks

Maybe this could help you a bit: [http://tldp.org/HOWTO/IP-Masquerade-HOWTO/iproute2.html](http://tldp.org/HOWTO/IP-Masquerade-HOWTO/iproute2.html)
and yes, you have to use iptables for this setup.

---

### Post by albox on 2008-02-07
I could not get it to work yet.
I wrote a script file that's loaded when booting :
```
EXTIF="eth0"
INTNET1="192.168.0.0/24"
EXTIP1="..."

modprobe ip_tables
modprobe ip_nat_ftp
modprobe iptable_filter
modprobe iptable_nat
iptables -F
iptables -X
iptables -t nat -A POSTROUTING -o $EXTIF -s $INTNET1 -j SNAT --to $EXTIP1
```


The rule has been set correctly :
> $ sudo iptables -t nat -n -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
SNAT       0    --  192.168.0.0/24       0.0.0.0/0           to:EXTERNAL_IP

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

However, the traffic is still going through the hub 192.168.0.254 instead of EXTERNAL_IP. Do you know what I'm doing wrong ?

Thanks

---

### Post by albox on 2008-02-10
Hi, I really need some help on this.

Do you have any clue about what's wrong ?
thanks

---

