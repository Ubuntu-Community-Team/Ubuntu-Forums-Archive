---
title: "what is the new networking?"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by scamper_22 on 2008-11-04
Hey all,

This may sound like a weird one.  I upgraded from Hardy to 8.10.
I finally managed to get my wireless working, but one thing I don't seem to have is the new wireless network selection.
examples from:  [http://www.dedoimedo.com/computers/ubuntu-8-10-review.html](http://www.dedoimedo.com/computers/ubuntu-8-10-review.html)

I DON'T HAVE THIS
[IMG]http://www.dedoimedo.com/images/computers/ubuntu-8.10-wireless-4.jpg[/IMG]

I DO HAVE THIS
But it is not useful as it only seems to allow me to configure wireless network manually... and confusingly at that... couldn't get it to work
[IMG]http://www.dedoimedo.com/images/computers/ubuntu-8.10-network-manager.jpg[/IMG]

As a result, I use wifi-radar to connect to my network.  How do I use the one above which looks very convenient?  Am I missing a package perhaps?  Or have I just missed some easy usability?

Cheers

---

### Post by pmsumner on 2008-11-04
CAn you post the output from running these commands in the terminal:

> iwconfig
ifconfig
cat /etc/network/interfaces


iwconfig shows the wireless config of network adapters
ifconfig shows the network settings of network adapters
cat /etc/network/interfaces prints out a text file containing information on how your network interfaces are configured

---

### Post by karlr42 on 2008-11-04
Obvious question, but have you left-clicked the network manager icon? That's what gives the first screenshot you posted

---

### Post by scamper_22 on 2008-11-04
Here's the output:
Please keep in mind there might be some legacy stuff in the config files as I've always struggled with wireless.  Once I get it working, I just leave it :)  Though I am sure it needs a cleanup.  

:~/system$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:09:57:7c  
          inet6 addr: fe80::20f:b0ff:fe09:577c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:946 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:656649 (656.6 KB)  TX bytes:143748 (143.7 KB)
          Interrupt:18 Base address:0x7000 

eth1      Link encap:Ethernet  HWaddr 00:90:4b:54:8b:9e  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe54:8b9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:91770 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62792 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:74390767 (74.3 MB)  TX bytes:11529426 (11.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1557 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1557 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:141791 (141.7 KB)  TX bytes:141791 (141.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-54-8B-9E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

XXXXXXX:~/system$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback



iface eth1 inet dhcp
pre-up ifconfig eth1 up
pre-up iwconfig eth1 rate 11M
wireless-key XXXXXXX
wireless-essid XXXXXX

auto eth1
:~/system$

---

### Post by scamper_22 on 2008-11-04
> **karlr42 said:**
> Obvious question, but have you left-clicked the network manager icon? That's what gives the first screenshot you posted

haha.  Ah, the old left click.  I was right clicking.  That was my other option... a usability thing.  Stupid me :P

Thanks!

Nonetheless, this is what I get.

I've attached the image of what happens when i left click.  It basically says the wireless is unmanaged and everything is disabled.  I assume this is because wifi-manager was used at first?

---

