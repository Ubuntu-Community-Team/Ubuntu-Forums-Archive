---
title: "Can not use ssh through Ethernet anymore"
date: 2023-06-22
forum: Networking &amp; Wireless
---

### Post by techmatt on 2023-06-22
Hello, I'm currently struggling with some problems trying to ssh my Raspberry Pi 3 to my Ubuntu 22.04. I don't have any chance to connect to my raspberry Pi over wifi and I also don't have any keyboard nor monitor to interface it. The only option left is trying to connect with ssh over Ethernet.
This is not the first time I do this and it has worked before, so my main problem is not really with my Raspberry but with my Ethernet interface.

A little bit more about the raspberry. I have set up in the past a telegram bot, that connects to the raspberry and give me the exact IP address of the board, both for the Ethernet port and the Wifi. So whenever I want to connect I just use the telegram bot to get the ethernet address and try to ssh it, but I get this error:


```
ssh: connect to host 169.254.38.195 port 22: No route to host
```

Before I go on I should mention that my friends try to connect with the same process but using different laptops, but using the same IP given by the telegram bot and it worked. So the problem lies in my computer. I have tried a lot of troubleshooting guides to fix my ethernet interface but nothing has worked. I've tried to restart the network manager, check if the drivers were updated, changed multiple times some of the settings of the ethernet port but nothing has worked so far. The only thing I didn't do is updating the kernel, but I want to avoid doing that now.

My guess is that the ethernet port is not being given an Ipv4 address, because when I run this commands I don't get any Ipv4 under the ethernet interface infos:

```
ifconfig
enp4s0f1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether 54:ab:3a:b5:db:2f  txqueuelen 1000  (Ethernet)
        RX packets 201  bytes 41875 (41.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 496  bytes 85990 (85.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 126  base 0xb000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 7598  bytes 880053 (880.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 7598  bytes 880053 (880.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.218.206.21  netmask 255.255.252.0  broadcast 10.218.207.255
        inet6 fe80::75b:c62b:3211:8764  prefixlen 64  scopeid 0x20<link>
        ether 54:8c:a0:a8:e4:95  txqueuelen 1000  (Ethernet)
        RX packets 82207  bytes 77203393 (77.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 38669  bytes 6491855 (6.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

I beg for your help, I am losing my mind :)

---

### Post by aljames2 on 2023-06-22
Have you checked your router settings.  Ethernet wired devices should all be configured with static IP addresses, and wifi connected devices should be configured to receive an IP via your DHCP service on your router or other such network management server.  Most routers allow you to set aside a range of IPs to be used by the DHCP server.

Have you tried to ping your gateway?

---

### Post by techmatt on 2023-06-23
I didn't check my router because I don't think this is related to what I want to do. I have a direct Ethernet cable from my pc to the raspberry, that doesn't bring internet connection, but it's just useful to execute ssh and open a console from my laptop.

---

### Post by QIII on 2023-06-23
Are you using a straight-through cable or a crossover cable?

---

### Post by techmatt on 2023-06-23
I am using a straight-through cable. We noticed that even using the straight-through cable it is working in Windows but non in Linux.

---

### Post by TheFu on 2023-06-23
> **techmatt said:**
> I didn't check my router because I don't think this is related to what I want to do. I have a direct Ethernet cable from my pc to the raspberry, that doesn't bring internet connection, but it's just useful to execute ssh and open a console from my laptop.

So ... the pi and computer aren't on any other network, but are directly connected with an ethernet cable?  No router?

Definitely no DHCP server.  Without DHCP, no IP will be assigned.  You'll have to configure that on the storage the PI uses.  The OS involved can have multiple different ways to configure an IP.

If the connection on 1 side isn't GigE or faster, then you have to use a cross-over cable to connect two computers.  

Additionally, you have to manually set the route between them, since there's no router to handle that.

If it were me, I'd go to a 2nd hand store and find any old router they have for $10, connect the Pi and your computer to that router, let it run a DHCP server and if it isn't too old, I'd setup a reserved IP through the DHCP-reservation capability.
[https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) - is a little old now, but with an old router, it might be the way. Newer routers have a pretty GUI for setting up DHCP reservations.

Without a router, even with an ethernet switch, you'll still need to setup the routes on each device to find the other.  It isn't hard, but it is a pain.  Get a router. Srsly.

---

