---
title: "Secondary IPs on different subnet"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by iLLiCiTgr on 2007-11-13
Hello everybody. I've been an ubuntu user for about 2 years so i know at least the basics.
I've got a dedicated server from i hosting company that came with 1 primary ip adress and 5 secondary ips. I've been trying to assign the secondary ips on my machine but alas, no luck!
It's probably a routing thing which i'm no good at (networking).

I've been assigned a primary Ip Address (Lets call it 78.XX.XX.19)

My Network Interface looks like this

```
# Loopback device:
auto lo
iface lo inet loopback

# device: eth0
auto eth0
iface eth0 inet static
  address 78.XX.XX.19
  broadcast 78.XX.XX.31
  netmask 255.255.255.224
  gateway 78.XX.XX.1


# default route to access subnet
up route add -net 78.XX.XX.0 netmask 255.255.255.224 gw 78.XX.XX.1 eth0

```

The server host sent me an email with some subnetwork ip

```
IP: 78.YY.YY.56
Mask: 255.255.255.248
Broadcast: 78.YY.YY.63
Useable IP addresses:
78.YY.YY.57 to 78.YY.YY.62

```
 
so i want to assign 78.YY.YY.57 to 78.YY.YY.62 as secondary ips for my server

After searching the web for a bit I tried adding something like

```
auto eth0:0
iface eth0:0 inet static
  address 78.YY.YY.57
  broadcast 78.YY.YY.63
  netmask 255.255.255.248
  gateway 78.XX.XX.1


auto eth0:1
iface eth0:1 inet static
  address 78.YY.YY.58
  broadcast 78.YY.YY.63
  netmask 255.255.255.248
  gateway 78.XX.XX.1
```

But as a read on other threads, some routing must take place.

First of all. Is what i'm trying possible? Are my subnet ip's usable or what?
Does it matter that my gateway is on a different subnet?

Thanks in advance for your replies.

---

### Post by iLLiCiTgr on 2007-11-13
I just received a pm from a friend of mine who suggested the following

Comment the decleration
#up route add -net 78.XX.XX.0 netmask 255.255.255.224 gw 78.XX.XX.1 eth0

cause it is somehow not needed.

also in my **ifconfig -a** i've got an eth0:1 up left from me trying to get it to work so an
**ipconfig eth0:1** down was in order

I tried to restart the networking and all the secondary interfaces eth0:1 to eth0:6 where up.

Out of curiosity. When i restart the networking, even when the virtual interfaces are up , the ip addresses are pingable an the server is reachable from these addresses, i get the following messages from **/etc/init.d/networking restart**

```
 * Reconfiguring network interfaces...                                          
SIOCDELRT: No such device
SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
                                                                         [ OK ]

```

What does it mean?

---

