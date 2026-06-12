---
title: "Poblems with my wired connection"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by Donut4277 on 2010-09-30
Ok so here is my issue. Forgive me I am a complete noob to Linux and command line
I am working on a old Dell Dimension C521. It was running windows Vista and contracted a virus. I couldn't get rid of it so I reformatted the hard drive and installed Ubuntu 10.04. Everything installed smoothly but now I am having an issue connecting to the Internet. 

I have the computer hooked up to a Motorala modem from Time Warner cable, SBV5220 SURFboard cable modem. The network shows up as Auto eth0. The problem is it will not connect to the network. It just automatically boots me off "you are now disconnected from the network". 

I have been trying different things but nothing seems to be working, also having problems because I have to thumb drive over any updates.

Let me know if you need any information on the computer.

ifconfig -a (this is what I get)
eth0      Link encap:Ethernet  HWaddr 00:1a:a0:09:19:e8  
          inet6 addr:fe80::21a:a0ff:fe09:19e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:894 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6737 errors:0 dropped:0 overruns:0 carrier:5
          collisions:0 txqueuelen:1000 
          RX bytes:58521 (58.5 KB) TX bytes:1184 (1.1 KB)
          Interrupt:19

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

Thanx in advance.

---

### Post by MooPi on 2010-09-30
Can you post the contents of /etc/network/interfaces

---

### Post by Donut4277 on 2010-09-30
You just comes up Permission denied for some reason

---

### Post by MooPi on 2010-09-30
Try this ```
gksu gedit /etc/network/interfaces
```

---

### Post by Donut4277 on 2010-09-30
it comes up with a window box that says interfaces (/etc/network) - gedit
Inside the window it says

auto lo
iface lo inet loopback

---

### Post by MooPi on 2010-09-30
Add theses lines:```
 # The primary network interface
auto eth0
iface eth0 inet dhcp
```
Then save and close. Then in terminal ```
sudo ifup eth0
```
If that doesn't work, reboot and check again.

---

### Post by Donut4277 on 2010-09-30
ok so in terminal after (sudo ifup eth0) it says:
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All Rights reserved
for info, please visit [https://www.isc.org/software/dhcp](https://www.isc.org/software/dhcp)

Listening on LPF/eth0/00:la:a0:09:19:e8
Sending on  LPF/eth0/00:la:a0:09:19:e8
Sending on  Socket/fallback
DHCPDISCOVER on eht0 to 255.255.255.255 prt 67 interval 5
DHCPDISCOVER on eht0 to 255.255.255.255 prt 67 interval 12
DHCPDISCOVER on eht0 to 255.255.255.255 prt 67 interval 14
DHCPDISCOVER on eht0 to 255.255.255.255 prt 67 interval 18
DHCPDISCOVER on eht0 to 255.255.255.255 prt 67 interval 10
DHCPDISCOVER on eht0 to 255.255.255.255 prt 67 interval 2
No DHCPOFFERS recieved.
No working leases in persistent database - sleeping

---

### Post by slooksterpsv on 2010-09-30
What kind of a router are you connecting to? What port are you on on that router? Do you have another available port you could try? How about a different ethernet cable?

If none of that works, try powercycling the router and see if that helps.

---

### Post by MooPi on 2010-09-30
Did you try the reboot ?

---

### Post by Donut4277 on 2010-09-30
Yes I did reboot. The only thing that has changed is not my network connection symbol is gone. I still cannot link to the Internet.

The router is a Motorala modem from Time Warner cable, SBV5220 SURFboard cable modem.
There is only one port on the router for an ether net cable.
I did try using a CAT6 cable instead of a CAT5 cable, and there was no change.

I am a bit of a noob and do not know how to powercycle the modem.

---

### Post by lswartz on 2010-09-30
> **Donut4277 said:**
> 

I am a bit of a noob and do not know how to powercycle the modem.

No problem, just pull power plug off your modem for about 30 seconds & then plug it back in.

---

### Post by Donut4277 on 2010-09-30
Oh. I wasnt sure what that was called.
I tried that several times and got nothing.

---

### Post by MooPi on 2010-09-30
Can you give us ```
ifconfig -a
``` and lets see if anything has changed ?

---

