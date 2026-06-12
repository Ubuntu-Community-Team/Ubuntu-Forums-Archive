---
title: "Ethernet network not configured in ubuntu 8.04"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by pdelahun on 2008-04-25
Hi gurus

Can anyone help me...

I have installed ununtu 8.04 on my new Acer Aspire 8920G. However the ethernet network card is not working. It seems that the wireless card is working just not the wired version. I have included the out put from. The same wired card works fine on windows vista. (default OS that came with the laptop)

lspci and ifconfig below:

lspci

02:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)
08:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

ifconfig

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63100 (61.6 KB)  TX bytes:63100 (61.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:84:8f:9f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-84-8F-9F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

It appears that the network card is from Attansic Technology Corp. And it says unknown device.

However under windows vista (i have dual boot) it says it is the card is Atheros AR8121/AR8113 PCI-E


Does anyone have any ideas what to do ????

---

### Post by Iowan on 2008-04-25
Post contents of **/etc/network/interfaces** If network was set up w/ Network Manager, I've read that only one interface can be active at a time.  You could either disable wireless and enable wired, or add an **auto eth0** line to aforementioned file.

---

### Post by pdelahun on 2008-04-25
Hi the output from 

cat /etc/network/interfaces

auto lo
iface lo inet loopback


if i change that to:
auto eth0

and run /etc/init.d/networking restart

then i get 

* Reconfiguring network interfaces...
Ignoring unknown interface eth0=eth0


Any ideas anyone ?

---

### Post by Monicker on 2008-04-25
You need your lo interface, so don't change that to eth0.  You would add an additional section for eth0.

Does eth0 show if you do "ifconfig -a"

---

### Post by Iowan on 2008-04-26
> **pdelahun said:**
> 02:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)


This doesn't look promising...

---

