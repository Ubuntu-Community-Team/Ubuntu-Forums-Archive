---
title: "Problems with NAT"
date: 2005-05-20
forum: Networking &amp; Wireless
---

### Post by esteryl on 2005-05-20
Hi! I'm trying to configure a shared internet connection in my computer.
I've made the following script
---------------------------------------------------------
#!/bin/sh

echo 'Configuring Firewall...'
# Insertando los modulos
modprobe iptable_nat
modprobe ipt_MASQUERADE

#Borrando todas las reglas
iptables -P INPUT ACCEPT
iptables -F INPUT
iptables -P OUTPUT ACCEPT
iptables -F OUTPUT
iptables -P FORWARD ACCEPT
iptables -F FORWARD
iptables -t nat -F

#Estableciendo reglas

echo 'Activating NAT...'
#Activa NAT
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
--------------------------------------------------------------
Simple, basic, but doesn't work!
I've used it in other debian machines and have allways worked propertly.

Where's the problem here? Should I make something else?
Network Interfaces are already configured, and both works.

Does anybody know what's missing?

---

### Post by fdoving on 2005-05-21
[QUOTE=esteryl]Hi! I'm trying to configure a shared internet connection in my computer.
I've made the following script
---------------------------------------------------------
#!/bin/sh

echo 'Configuring Firewall...'
# Insertando los modulos
modprobe iptable_nat
modprobe ipt_MASQUERADE

#Borrando todas las reglas
iptables -P INPUT ACCEPT
iptables -F INPUT
iptables -P OUTPUT ACCEPT
iptables -F OUTPUT
iptables -P FORWARD ACCEPT
iptables -F FORWARD
iptables -t nat -F

#Estableciendo reglas

echo 'Activating NAT...'
#Activa NAT
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
--------------------------------------------------------------
Simple, basic, but doesn't work!
I've used it in other debian machines and have allways worked propertly.

Where's the problem here? Should I make something else?
Network Interfaces are already configured, and both works.

Does anybody know what's missing?[/QUOTE]
 Can't see why this shouldn't work.
I've been using theese simple lines:

----start---
#!/bin/bash
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
---stop---

And it worked perfectly. My kernel automatically loaded the needed modules and all.

- Frode

---

### Post by accmariano on 2005-05-26
Hi, 

I don't know if that help but...

How do you connect to internet? Don't you do that through PPP over ethernet or something like this?

If  yes you should change masquerade commant to:

iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

where ppp0 is your internet connection

Bye
Mariano

[QUOTE=esteryl]Hi! I'm trying to configure a shared internet connection in my computer.
I've made the following script
---------------------------------------------------------
#!/bin/sh

echo 'Configuring Firewall...'
# Insertando los modulos
modprobe iptable_nat
modprobe ipt_MASQUERADE

#Borrando todas las reglas
iptables -P INPUT ACCEPT
iptables -F INPUT
iptables -P OUTPUT ACCEPT
iptables -F OUTPUT
iptables -P FORWARD ACCEPT
iptables -F FORWARD
iptables -t nat -F

#Estableciendo reglas

echo 'Activating NAT...'
#Activa NAT
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
--------------------------------------------------------------
Simple, basic, but doesn't work!
I've used it in other debian machines and have allways worked propertly.

Where's the problem here? Should I make something else?
Network Interfaces are already configured, and both works.

Does anybody know what's missing?[/QUOTE]

---

