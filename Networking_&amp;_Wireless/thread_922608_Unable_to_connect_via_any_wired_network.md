---
title: "Unable to connect via any wired network"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by stillnew on 2008-09-17
I have an on board ethernet adapter that functioned all summer.  I was unable to connect to school internet.  Because I was unable to even hand the computer an IP from a router, I purchased and installed a NIC (Trendnet TE100-PCIWN) which was able to connect on my first boot after install but not since.

I have tried connecting to my linksys router and unable to establish connect with either the on board or trendnet adapter.

I have used a different computer to verify that connections are possible to both the campus network and the router, and that the cables are good.

I also tried booting with the live CD to see if that could connect, but it was also unable to establish any connections.

What should I do to connect?

---

### Post by Iowan on 2008-09-17
Post results of **ifconfig** and contents of **/etc/network/interfaces**.  An avahi address means DHCP failed.

---

### Post by stillnew on 2008-09-17
For ifconfig:
> eth0      Link encap:Ethernet  HWaddr 00:1f:c6:1a:7c:ca  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:14:d1:51:ed:14  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:5206 dropped:7646 overruns:5206 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xac00 

eth1:avahi Link encap:Ethernet  HWaddr 00:14:d1:51:ed:14
          inet addr:169.254.6.194  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST MTU:1500  Metric:1
          Interrupt:17 Base address:0xac00

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:316 errors:0 dropped:0 overruns:0 frame:0
          TX packets:316 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16184 (15.8 KB)  TX bytes:16184 (15.8 KB)


/etc/networks/interfaces:
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface, added manual, not by a configure program

iface eth0 inet dhcp


iface eth1 inet dhcp

auto eth1


eth1 is the Trendnet NIC, i get similar results if i plug into eth0, the on board adapter.  This is all connected to campus internet not my router.

---

### Post by Iowan on 2008-09-17
I doubt it's the solution, but if you have "roaming" selected, try unchecking it and restart networking (**sudo /etc/init.d/networking restart)**.

---

### Post by stillnew on 2008-09-17
Yeah, roaming is off.  It is set to dhcp.

---

### Post by stillnew on 2008-09-29
Is there really nobody with any other ideas as to what the problem could be?

---

### Post by superprash2003 on 2008-09-29
try static ip and see if that works..

---

### Post by shandiddy on 2008-09-29
I am having the same problem this **"avahi"** thing is the plague of my life.  I tried ```
sudo ifconfig eth0:avahi down
``` it removed the avahi from ifconfig but upon restart there is still no internet connection and that avahi comes back.

---

