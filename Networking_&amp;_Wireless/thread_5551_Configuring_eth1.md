---
title: "Configuring eth1"
date: 2004-11-19
forum: Networking &amp; Wireless
---

### Post by KLineD on 2004-11-19
Hi, I've been trying Ubuntu and the installation detected only my eth0 NIC, it connects fine to the Internet. I tried to manually configure my eth1 NIC editing the /etc/network/interfaces file

I just added the lines:
auto eth1
iface eth1 inet static
        address 192.168.0.1
        netmask 255.255.255.0
	gateway 10.29.64.1

when I restart the network using /etc/init.d/networking start it says "Ok". Using ifconfig says that eth0 and eth1 are configured, but my internet connection doesn't work, I tried to ping anything but with no response. The only way to get internet connection again is by removing the 'auto' word in the 'auto eth1' line of the interfaces file, but then if I restart the network it wont start the eth1 nic.

What am I doing wrong???

Thanks a lot.

---

### Post by arctic on 2004-11-19
in case you use a router: have you tried setting the eth from static to dhcp?

---

### Post by KLineD on 2004-11-19
Hi, thanks for your reply
No I dont use a router, eth0 is connected to my cablemodem and eth1 is used with a crossover cable to connect my pc with my xbox

---

### Post by FLeiXiuS on 2004-11-19
You need a route to the internet IP.  

```
man route
```  

There's no easy way of explaining it without seeing it your self.

---

### Post by KLineD on 2004-11-20
Ok I tried the following
route add -host <<my host>>  netmask 255.255.192.0 dev eth0

as the output from ifconfig says:
eth0      Link encap:Ethernet  HWaddr 00:40:F4:14:11:21
          inet addr:10.29.64.79  Bcast:255.255.255.255  Mask:255.255.192.0
          inet6 addr: fe80::240:f4ff:fe14:1121/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:414 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1542003 (1.4 MiB)  TX bytes:111963 (109.3 KiB)
          Interrupt:201 Base address:0xc800

No matter what I put in the <<my host>> section all I get is some waiting and then route tells me that the name of the host was not found. What's the host and where can I find that information?? 
Thanks!

---

### Post by KLineD on 2004-11-21
Just to point out that I figured it out
In the interfaces file I configure eth1 as static and then restart the network, now my computer couldnt connect to the internet, so i did a ifdown eth1 and then I could connect. Next I did a ifup eth1 and the system would complain about something but still bring up the NIC and still could connect to the internet. The next time I booted everything was correctly configured, mi internet connection and my eth1 nic

---

