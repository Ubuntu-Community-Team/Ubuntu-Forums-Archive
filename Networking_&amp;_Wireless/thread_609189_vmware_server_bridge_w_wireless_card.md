---
title: "vmware server bridge w/ wireless card"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by hasimir44 on 2007-11-10
I'm using vmware server to run an instance of XP on my laptop for 2 reasons: 
1. to connect to my work's vpn :(
2. to have my own private (portable) WoW server :)

I couldn't find any exact answers for how to make a vmware guest accessible to outside hosts if you're only using a wireless card on the vmware host.  Using a vmware bridge works great to a wired card, but I read that this does NOT work with 99% of wireless cards.. 

Anyway, I got this working so I wanted to share it.. I'm no network or security pro,  but this works for me.

Run the vmware-config.pl script and setup a "host only" interface in the networking section.  I just let it search for an unused subnet (172.16.157.0). 

Start up vmware and make sure that your vm host is using that interface. VM ->  Settings  -> should show an Ethernet interface that says "Host-only" in the summary.

Then setup iptable rules to forward from the vmnet interface to your wireless card w/ ip masquerading. I used the following script (must run as root): 

```

#!/bin/bash

WIRELESS="eth1"
echo "1" > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o $WIRELESS -j MASQUERADE
iptables -A FORWARD -j ACCEPT


```  

Setup a static IP on the vmware guest from within the "unused" subnet that the vmware-config.pl script generated. I used the following (gateway: ifconfig vmnet1), (dns server: nslookup [www.google.com](www.google.com)) :

```
 
IP:  172.16.157.10
SUBNET: 255.255.255.0
GW:  <vmnet1 ip>
DNS: <dns server>

```

I had to add a route to the vm machine's subnet on each box in my lan that needs to access it (the first IP is the vmnet1's subnet, the second is the IP of the vmware host (physical box that vmware server is running on): 

```
route add 172.16.157.0    192.168.1.102
```

that's it..

---

### Post by K.Mandla on 2007-11-14
Moved to Networking and Wireless.

---

### Post by keskew on 2007-11-15
I found another solution on the thread below.

[http://ubuntuforums.org/showthread.php?p=3772591]("http://ubuntuforums.org/showthread.php?p=3772591")

---

### Post by Divan Santana on 2008-05-18
Awesome thread! Thanks for posting this :)
I just used it and it works great :)

---

