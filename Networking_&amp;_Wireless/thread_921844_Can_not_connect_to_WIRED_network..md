---
title: "Can not connect to WIRED network."
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by raley on 2008-09-16
I just installed Ubuntu and got it working last night.  I read that I should be able to just plug in the ethernet cable to the linksys router and to the laptop and it should work. nothing.  So I clicked on the network icon and changed it to DHPC (or what ever the letter order is) and still nothing.

Here are the specs on the machine: it is an Acer Aspire 5050-5430

	
	  Processor Brand:  	AMD
	  Processor Class:  	Athlon™ 64 X2 Dual-Core TK-53
	  Processor Speed:  	1.7GHz
	  Processor FSB:  	up to 1600MHz
	  Processor Cache:  	2 x 256KB L2
	
	  Memory Type:  	DDR2
	  Memory Size:  	1GB (512MB x 2)
	  Memory Speed:  	DDR2 533
	  Maximum Memory Supported:  	4GB
	  Capacity:  	120GB
	
	  GPU/VPU:  	ATI Radeon Xpress 1100
	
	  Communications Description:  	Integrated LAN
	  	Integrated Modem
	  	Integrated Wireless LAN
	  Interface Type:  	RJ-11 Phone Connector
	  	RJ-45 Ethernet Connector
	  	Acer InviLink 802.11b/g wireless LAN
	  Data Transfer Rate:  	10/100Mbps NIC
	  	56Kbps Modem
	  	54 Mbps
	
	  Protocols:  	V.92
	  	802.11b
	  	802.11g

Is there some setting somewhere that I missed in my reading?

Thank you all for helping.
Raley

---

### Post by Iowan on 2008-09-16
Did you restart networking after changing to DHCP? (**sudo /etc/init.d/networking restart**)
If so, post results of **ifconfig** and contents of **/etc/network/interfaces** file.

---

### Post by raley on 2008-09-16
> 
[COLOR="Red"]ifconfig[/COLOR]:

eth0 Link encap:Ethernet  HWaddr 00:1b:24:9d:fd:47
     inet6 addr: fe80::21b:24ff:fe9d:fd47/64 Scope:Link
     UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:26 errors:0 dropped:0 overruns:0 frame:0
     collisions:0 txqueuelen:1000
     RX bytes:0 (0.0 B)  TX bytes:4015 (3.9 KB)
     Interrupt:16 Base address:0xa000

eth0:avahi Link encap:Ethernet HWaddr 00:1b:24:9d:fd:47
          inet addr:169.254.7.146 Bcast:169.254.255.255 Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          Interrupt:10 Bass address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:14370 (14.0 KB)  TX bytes:14370 (14.0 KB)


> 
[COLOR="Red"]/etc/network/interfaces[/COLOR]:
Permission denied


That was lots of typing.  and restarting the settings did not work.

---

### Post by Iowan on 2008-09-17
Copy/paste works well (via pulldown options. CTRL-C/CTRL-V... not so good).
The avahi address means DHCP did not succeed. I'll see if I can find some links to similar threads.

That **permission denied** message on **/etc/network/interfaces**... did you try to execute the file or list it?

---

