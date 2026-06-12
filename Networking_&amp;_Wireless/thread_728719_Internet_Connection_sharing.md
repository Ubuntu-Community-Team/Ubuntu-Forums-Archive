---
title: "Internet Connection sharing"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by rabosajr on 2008-03-19
Hey guys need your help here. I have two PC's running on Kubuntu Gutsy. One has two network cards; eth0 is connected to the internet, while eth2 is wired to a hub. The second PC has one network card eth0 connected to the hub. 

I want the second PC to share my internet connection but I can't seem to get it to work.

I am able to PING the two PC's from one another. However, I am not able to browse from firefox in the second PC. Firefox works fine in the first PC.

Running ifconfig, have the following:

PC One

eth0      Link encap:Ethernet  HWaddr 00:03:6D:1B:EB:41
          inet addr:192.168.255.252  Bcast:192.168.255.255  Mask:255.255.224.0
          inet6 addr: fe80::203:6dff:fe1b:eb41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25436 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4571201 (4.3 MB)  TX bytes:410845 (401.2 KB)
          Interrupt:3 Base address:0xd800

eth2      Link encap:Ethernet  HWaddr 00:1C:F0:65:B4:F9
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:f0ff:fe65:b4f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1206 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:140975 (137.6 KB)  TX bytes:10041 (9.8 KB)
          Interrupt:10 Base address:0x4800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:88 (88.0 b)  TX bytes:88 (88.0 b)

PC Two

eth0      Link encap:Ethernet  HWaddr 00:00:E2:96:A1:6A
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:e2ff:fe96:a169/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2466 (2.4 KB)  TX bytes:5413 (5.2 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Thanks!

---

### Post by SpaceTeddy on 2008-03-19
since you already have the basic setup that the two pc's can find each other, you only need to enable ip-forwarding and nat. i've written down a few steps on how to do this previously -  you can probably skip the ones about network card setup if you can already ping the computers...

[here]("http://ubuntuforums.org/showthread.php?t=713874") is the steps i've written down.

hope you get it to work :)

---

### Post by rabosajr on 2008-03-19
Thanks for the reply. I'll give a go later today.

---

### Post by rabosajr on 2008-03-24
SpaceTeddy thanks for the post but it didn't work form me though.

I tried firestarter, internet connection is now shared.

---

### Post by SpaceTeddy on 2008-03-24
can you please post the output of the following commands to (hopefully) figure out what the problem is - or why it didn't work

from the machine sharing
```
sudo iptables -L -vnx
sudo iptables -L -vnx --table nat
ifconfig
route -n
cat /proc/sys/net/ipv4/ip_forward
```

from the machine that wants to use the internet
```
route -n
sudo iptables -L -vnx
ifconfig
```

thanks :)

---

