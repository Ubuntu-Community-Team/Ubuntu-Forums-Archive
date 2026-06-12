---
title: "[SOLVED] Server access problem"
date: 2007-12-24
forum: Networking &amp; Wireless
---

### Post by Rich930 on 2007-12-24
:confused:hi, you may have seen my other post, but id thought id make new one

basicallly, i just hooked my server up to my router (WMP54G) but i cant access it from any machine wirelessly.

I went into "sudo nano /etc/network/interfaces"
and changed the ateway to 192.168.1.1 (my routers ip adress) and the servers static ip is 192.168.0.3.  but i cant find it anywhere on the network.

please help me :)

thanks

---

### Post by burbankmarc on 2007-12-24
from your server are you able to ping your router? I'd say no if your gateway address is 192.168.1.1, and your server ip is 192.168.0.3. 

If you can, give me the contents of a 
```
route -n
```

---

### Post by Rich930 on 2007-12-24
no i cant, i changed it, the gateway was originally 192.168.0.1. now, like i said i changed it to the router's ip adress 192.168.1.1.

route -n:
Kernel IP routing table

Destination:     
192.168.0.0
Gateway:
0.0.0.0 
Genmask: 
255.255.255.0
Flags:
U
Metric :
0
Ref:  
0
Use: 
0
Iface:
eth0


this confused me,, why do i now have no gateway, this isnt what it says in  /etc/network/interfaces   

thanks

---

### Post by burbankmarc on 2007-12-24
Essentially your 2 boxes need to be on the same subnet to communicate. 

for example:

if your router is 192.168.1.1/24 and your server is 192.168.0.3/24 they are NOT on the same subnet

a /24 address means that the last octet is all the hosts. so 192.168.1.1-254 is the same subnet, and 192.168.0.1-254 is a different subnet.

they need to BOTH be on the same /24, unless you want to change it to a /16 subnet.

---

### Post by Rich930 on 2007-12-28
thanks, ill try that, but it doesnt have /24 or -254 after any of the adresses to begin with. 

bit confused. :S

---

