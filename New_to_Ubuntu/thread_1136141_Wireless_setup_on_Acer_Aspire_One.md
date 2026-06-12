---
title: "Wireless setup on Acer Aspire One"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by jrlii on 2009-04-24
The other day I bought an Acer Aspire One, and after a few adventures got Intrepid installed, and I'm now trying to get the wiresless to go.

Do I have to use a hard wire ethernet cable to get the newtorking going before I can set up the wireless?

Some time back there was a thread on a similar-but-not-identical 'puter and it looked like his problems were resolved, but exactly how wasn't clear.

Here is the output of sudo dhclient:

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/pan0/de:f7:4e:ff:e4:c2
Sending on   LPF/pan0/de:f7:4e:ff:e4:c2
Listening on LPF/eth0/00:23:8b:90:f3:ff
Sending on   LPF/eth0/00:23:8b:90:f3:ff
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

and the outpuf from iconfig:

eth0      Link encap:Ethernet  HWaddr 00:23:8b:90:f3:ff  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:2774783689 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 

eth0:avahi Link encap:Ethernet  HWaddr 00:23:8b:90:f3:ff  
          inet addr:169.254.11.177  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1104 (1.1 KB)  TX bytes:1104 (1.1 KB)

pan0      Link encap:Ethernet  HWaddr de:f7:4e:ff:e4:c2  
          inet6 addr: fe80::dcf7:4eff:feff:e4c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:7921 (7.9 KB)

pan0:avahi Link encap:Ethernet  HWaddr de:f7:4e:ff:e4:c2  
          inet addr:169.254.11.235  Bcast:169.254.255.255  Mask:255.255.0.0

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
And the output from lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by Aearenda on 2009-04-24
Yes, you'll need to be wired first. The instructions for madwifi at [this page]("https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Intrepid%20Ibex%208.10%20on%20the%20Acer%20Aspire%20One") worked with Intrepid on my AA1.

---

### Post by jrlii on 2009-04-24
Thanks! I'll give that a try as soon as I can borrow a wired connection. (At home I'm still on dial up.)

Sounds like there is about enough info in that link to make the li'l varment just about perfect!

---

