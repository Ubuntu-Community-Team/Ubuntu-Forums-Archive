---
title: "[SOLVED] Ubuntu on usb drive"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by tsucol11 on 2008-11-11
Present configuration is: 

A8NSLI motherboard with onboard Marvell tech 88E8001 gig Ethernet controller, connected to a D-link green (DGS10008D) switch connected to a SMC barricade router. 

Router supplies DCHP. System works fine for XP Pro and Mandriva 2008 (previously on the same USB drive), connection to the internet works automatically.

installed Ubuntu 8.10. It recognizes the Marvell tech Ethernet controller but does not want to connect to the switch/router to get a network address. I cannot connect to the internet much less to the network. 

Could the fact that the installation is on a UBD drive (120gig)be the problem??

Read the help file but no help.

Decided to try Ubuntu as a friend of mine has it installed on various machines including laptops without any issues 

Thanks for any help in getting the Ethernet controller recognized. 

Brian

---

### Post by superprash2003 on 2008-11-11
post output of ifconfig from the terminal.

---

### Post by tsucol11 on 2008-11-11
> **superprash2003 said:**
> post output of ifconfig from the terminal.

brian@brian-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:2f:a8:9c:65  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1007 (1.0 KB)  TX bytes:0 (0.0 B)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15632 (15.6 KB)  TX bytes:15632 (15.6 KB)


Thanks

Brian

---

### Post by tsucol11 on 2008-11-11
brian@brian-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:2f:a8:9c:65  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1007 (1.0 KB)  TX bytes:0 (0.0 B)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15632 (15.6 KB)  TX bytes:15632 (15.6 KB)

Thanks

Brian

---

### Post by superprash2003 on 2008-11-12
how about manually trying to assign a static ip instead of DHCP..by editing the /etc/network/interfaces file

---

### Post by tsucol11 on 2008-11-12
> **tsucol11 said:**
> Present configuration is: 

A8NSLI motherboard with onboard Marvell tech 88E8001 gig Ethernet controller, connected to a D-link green (DGS10008D) switch connected to a SMC barricade router. 

Router supplies DCHP. System works fine for XP Pro and Mandriva 2008 (previously on the same USB drive), connection to the internet works automatically.

installed Ubuntu 8.10. It recognizes the Marvell tech Ethernet controller but does not want to connect to the switch/router to get a network address. I cannot connect to the internet much less to the network. 

Could the fact that the installation is on a UBD drive (120gig)be the problem??

Read the help file but no help.

Decided to try Ubuntu as a friend of mine has it installed on various machines including laptops without any issues 

Thanks for any help in getting the Ethernet controller recognized. 

Brian

PROBLEM SOLVED

From JFo NZ, solved my problem. Needed both code lines.

 Re: No Ethernet in Intrepid Ibex
After upgrading to 8.10 my ethernet stopped. You might have the same problem. This is how I fixed it.

Edit /etc/network/interfaces

Code:

sudo gedit /etc/network/interfaces

Add 2 new lines to "/etc/network/interfaces"

Code:

auto eth0
iface eth0 inet dhcp

Then restart machine. Fixed.
JFo NZ is offline Report Post   	Reply With Quote

Appears to be working OK now.

Brian

---

