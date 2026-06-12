---
title: "eth1 acting strange"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by rgb96 on 2009-02-18
Hey guys and gals,

I've got two NICs in my computer, and I can't seem to get eth1 to work. In fact, when eth1 is up, I can't get internet at all. When I did a dmesg, I got this line about 100 times:

```
[  318.171412] eth1: Autonegotiation failed, using 10baseT, link beat status 70cc.

```

So I tried using ethtool to change it to speed 100 duplex full autoneg off, (which is how I want it) but I just get this error:

```
x@y:~$ sudo ethtool eth1
Settings for eth1:
No data available

```

Any ideas?

---

### Post by rgb96 on 2009-02-18
Also, if I try putting eth0 down and eth1 up I get this
```
x@y:~$ sudo ifdown eth0
x@y:~$ sudo ifup eth1
 * if-up.d/mountnfs[eth1]: waiting for interface eth0 before doing NFS mounts
```

what does that even mean?

---

### Post by superprash2003 on 2009-02-18
post output of **ifconfig** and post contents of /etc/network/interfaces.. have you tried restarting networking **sudo /etc/init.d/networking restart **

---

### Post by rgb96 on 2009-02-18
```
x@y:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:6e:bb:a0:68  
          inet addr:10.2.71.237  Bcast:10.2.71.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:febb:a068/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10772 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8607262 (8.6 MB)  TX bytes:2301103 (2.3 MB)
          Interrupt:22 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1668 (1.6 KB)  TX bytes:1668 (1.6 KB)

x@y:~$ sudo gedit /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 10.2.71.237
	network 10.2.71.0
	netmask 255.255.255.0
	broadcast 10.2.71.255
	gateway 10.2.71.254

auto eth1
iface eth1 inet static
	address 10.2.71.236
	network 10.2.71.0
	netmask 255.255.255.0
	broadcast 10.2.71.255
	gateway 10.2.71.254




```

Yeah, tried that already.

---

### Post by superprash2003 on 2009-02-19
why do you have 2 NICS both pointing to the same gateway?? and dont put them on the same subnet mask

---

