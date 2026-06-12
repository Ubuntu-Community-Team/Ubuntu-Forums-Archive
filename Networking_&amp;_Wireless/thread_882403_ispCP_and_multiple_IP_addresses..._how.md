---
title: "ispCP and multiple IP addresses... how?"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by chrisoverly on 2008-08-06
Hello, I am new to linux and am playing with Ubuntu and ispCP which is a VHCS fork. I figure if I force myself to run my own server I will learn faster.

My question is how do I set my second IP address (i already set my first ip at setup) and get both of them to reverse dns to ns1.mydomain.com and ns2.mydomain.com

any help would be much appreciated, chris

---

### Post by SpaceTeddy on 2008-08-07
> ispCP which is a VHCS fork
i have no idea what that is. 

But if you question is how you can add a second ip address to a network cards - you have to define a virtual device which uses your real network cards. For example, if you want to attach a second ip to eth0, you would use the configuration:

```
iface eth0:0 inet static
	address 123.123.123.123
	netmask 255.255.255.0

```

just add that to your /etc/network/interfaces and run
```
ifconfig eth0:0 up
```
which should give you a second ip attached to eth0 with the virtual device eth0:0

i hope this is what you were asking for... :)

---

### Post by chrisoverly on 2008-08-07
My problem is I do not know how to get to the point that you mentioned

Thanks, Chris

---

### Post by SpaceTeddy on 2008-08-07
mhm - how are you configuring your network cards ? 
also can you please post the output of

> cat /etc/network/interfaces
ifconfig

thanks a lot

---

### Post by chrisoverly on 2008-08-08
root@blazecom:/home/chris# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 207.119.89.114
        netmask 255.255.255.248
        network 207.119.89.112
        broadcast 207.119.89.119
        gateway 207.119.89.113
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 207.119.89.113 208.67.220.220
        dns-search 1224broadway.com
root@blazecom:/home/chris# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:2b:69:f2:37
          inet addr:207.119.89.114  Bcast:207.119.89.119  Mask:255.255.255.248
          inet6 addr: fe80::240:2bff:fe69:f237/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32733 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12007 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2669115 (2.5 MB)  TX bytes:2041823 (1.9 MB)
          Interrupt:20 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5934 (5.7 KB)  TX bytes:5934 (5.7 KB)

root@blazecom:/home/chris#

---

