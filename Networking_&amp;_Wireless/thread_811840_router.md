---
title: "router"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by PhDP on 2008-05-29
Simple config; 

I have a router with 3 computers connected to it; 

- A standard Laptop with WINXp

- The computer I'm using right now (WINXp)

- I'm trying to use my Ubuntu laptop, but to no avail. It seems to see the wired connection, but it just don't want to access internet.

---

### Post by jimv on 2008-05-29
With your laptop connected to the router, type ifconfig in the terminal and then post the output here.

---

### Post by PhDP on 2008-05-29
eth0      Link encap:Ethernet  HWaddr 00:1D:09:58:38:AA  
          inet6 addr: fe80::21d:9ff:fe58:38aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58401 errors:0 dropped:0 overruns:0 frame:0
          TX packets:544 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1 txqueuelen:1000 
          RX bytes:3818446 (3.6 MB)  TX bytes:38415 (37.5 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1F:3C:54:C7:35  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:844 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Memory:f9fff000-f9ffffff 

eth0:avah Link encap:Ethernet  HWaddr 00:1D:09:58:38:AA  
          inet addr:169.254.5.106  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:218 errors:0 dropped:0 overruns:0 frame:0
          TX packets:218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21108 (20.6 KB)  TX bytes:21108 (20.6 KB)

---

### Post by superprash2003 on 2008-05-29
go to system->administration->network and choose either eth0 or eth1 properties( whichever is connected to the router) and change it from roaming mode to DHCP mode and then post ifconfig output

---

### Post by PhDP on 2008-05-29
Sorry but I have no idea what you mean by "choose either eth0 or eth1 properties", I chose the icon for wired connections, then DHCP mode, and the ifconfig is;

eth0      Link encap:Ethernet  HWaddr 00:1D:09:58:38:AA  
          inet6 addr: fe80::21d:9ff:fe58:38aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56662 errors:0 dropped:0 overruns:0 frame:0
          TX packets:989 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3733185 (3.5 MB)  TX bytes:74321 (72.5 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1F:3C:54:C7:35  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:21643 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Memory:f9fff000-f9ffffff 

eth0:avah Link encap:Ethernet  HWaddr 00:1D:09:58:38:AA  
          inet addr:169.254.5.106  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1890 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1890 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:185912 (181.5 KB)  TX bytes:185912 (181.5 KB)

---

### Post by jimv on 2008-05-30
It's pulling down an IPv6 address on eth0...anyone have any ideas on that?

---

### Post by PhDP on 2008-05-30
It's surprising that I get such a strange error, the first thing I tried to do with my laptop, a standard XPS M1330 laptop with Ubuntu 7.10, was to make the internet work.

Nothing was installed and my internet connection work very well...

---

### Post by fwre01 on 2008-05-30
can you paste the output from the command "cat /etc/network/interfaces"?

---

### Post by PhDP on 2008-05-30
What do you mean, I'm supposed to type that in the terminal ?

If yes; I got;

bash: cat/etc/network/interfaces: No such file or directory

---

### Post by fwre01 on 2008-05-30
yes, sorry, in a terminal

there is a space after the word cat

---

### Post by PhDP on 2008-05-30
ops, I saw the space, I thought it was a typo, sorry. I got; 

auto lo
iface lo inet loopback



iface eth0 inet dhcp

auto eth0

---

### Post by fwre01 on 2008-05-30
It seems as tho you have a wireless connection on eth0. and eth1 is your wired interface (i think it numbers them based on the MAC address, someone may correct me on that) and eth1 has no config in your interfaces file

type this command in a terminal
```
 sudo gedit /etc/network/interfaces 
```

then replace the existing text with the following

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp 
```

Save the file and reboot your machine, this should fix it

---

### Post by PhDP on 2008-05-30
It doesn't work.

Now when I type cat /etc/network/interfaces I get; 

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

I even tried to shut my internet connection for 1 minutes and tried again...

> **fwre01 said:**
> It seems as tho you have a wireless connection on eth0. and eth1 is your wired interface (i think it numbers them based on the MAC address, someone may correct me on that) and eth1 has no config in your interfaces file

For now, the wireless doesn't matter, I just want my normal connection to work :(

---

### Post by fwre01 on 2008-05-30
Ok, type
```
 sudo dhclient 
```
and then paste the output from ```
 ifconfig 
```

---

### Post by PhDP on 2008-05-30
sudo dhclient

Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1f:3c:54:c7:35
Sending on   LPF/eth1/00:1f:3c:54:c7:35
Listening on LPF/eth0/00:1d:09:58:38:aa
Sending on   LPF/eth0/00:1d:09:58:38:aa
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.



ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1D:09:58:38:AA  
          inet6 addr: fe80::21d:9ff:fe58:38aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4818 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:312830 (305.4 KB)  TX bytes:14992 (14.6 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1F:3C:54:C7:35  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:335 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x4000 Memory:f9fff000-f9ffffff 

eth0:avah Link encap:Ethernet  HWaddr 00:1D:09:58:38:AA  
          inet addr:169.254.5.106  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

eth1:avah Link encap:Ethernet  HWaddr 00:1F:3C:54:C7:35  
          inet addr:169.254.5.185  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x4000 Memory:f9fff000-f9ffffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2680 (2.6 KB)  TX bytes:2680 (2.6 KB)

---

### Post by fwre01 on 2008-05-30
Im assuming theres a link light on the interface and on the router port its connected to?

have you tried a different cable? or in a different "known" working router port?

---

### Post by PhDP on 2008-05-30
Yes I did, but I think I'll try to connect my laptop directly to the modem, shut both the laptop and the modem for a minute and see what happens.

---

### Post by fwre01 on 2008-05-30
OK, well let me know how you get on, the output you are seeing is usually when there is no layer 1 connection, or (as the DHCP output is saying) your getting no offer from the router

---

### Post by PhDP on 2008-05-30
Ye ! I'm writing this post from my laptop, it works great !

Thank you a lot !

---

### Post by fwre01 on 2008-05-30
ahh great! have fun!

---

