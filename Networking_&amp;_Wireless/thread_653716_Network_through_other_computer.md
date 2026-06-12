---
title: "Network through other computer"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by stroumf on 2007-12-30
Hallo and many wishes to all.
I have a laptop an a desktop. I am tryin to go out to internet from laptop through the desktop.
laptop ip: 192.168.1.13 gw 192.168.1.10
desktop : ethernet 192.168.1.10 wireless 192.168.178.2
router 192.168.178.1

root@ubumanin:/# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.178.1   0.0.0.0         255.255.255.255 UH    0      0        0 eth0
192.168.178.0   192.168.178.1   255.255.255.0   UG    0      0        0 eth0
192.168.1.0     192.168.1.10    255.255.255.0   UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.8     0.0.0.0         UG    100    0        0 eth0  

root@ubumanin:/# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:38:3E:FE:7F
          inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe3e:fe7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4003 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:410355 (400.7 KB)  TX bytes:411129 (401.4 KB)
          Interrupt:18 Base address:0xa000   

I can't see 192.168.178.0 network. Why?
Thanks a lot

---

### Post by foolsh on 2007-12-31
Is the Desktop box running ubuntu?
if so an easy way to do this
```
sudo apt-get install dnsmasq ipmasq firestart
```
on the desktop
then
```
sudo firestarter
```
and run through the wizard enabling then Internet Connection Sharing
dont forget to allow connections from your local network
192.168.1.0/16
firestarter is an easy to use iptables configuration utility I would recommend putting on all your ubuntu computers.

---

### Post by stroumf on 2008-01-03
I couldn 't install firestarter.
It couldn't find it.

---

### Post by Predator[23rd] on 2008-01-03
what have you entered in the routing table? can you recap the commands? it looks like you have not setup a route between 192.168.1.0 and 192.168.178.0 ... or am I mistaken?

---

