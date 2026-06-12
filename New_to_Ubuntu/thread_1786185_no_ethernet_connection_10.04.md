---
title: "no ethernet connection 10.04"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by Clive Richardson on 2011-06-19
Have recently finished installing ubuntu 10.04.1 but am unable to establish an wired internet connection. I have made sure it is 'enabled' and have tried rebooting. I would be very grateful for any help.
Having seen other threads I have prepared the following information as each computer seems to have its individual problems. Comparing these results to those from my 8.04 version, I think the problem may be to do with RX & TX packets but have no idea what these are. 
I did post a similar message on the Installation Forum two days ago but haven't had any replies, so am hoping someone can help here.
desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:09.0 USB Controller: NEC Corporation USB (rev 41)
00:09.1 USB Controller: NEC Corporation USB (rev 41)
00:09.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
00:0c.0 Communication controller: Conexant Systems, Inc. HCF 56k Data/Fax/Voice Modem (rev 0
00:0d.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
00:0e.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 07)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS
desktop:~$ sudo lshw -C network
*-network
description: Ethernet interface
product: DP83815 (MacPhyter) Ethernet Controller
vendor: National Semiconductor Corporation
physical id: d
bus info: pci@0000:00:0d.0
logical name: eth0
version: 00
serial: 00:02:e3:24:51:b5
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half latency=64 link=no maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=10MB/s
resources: irq:5 ioport:d000(size=256) memory:dfffc000-dfffcfff memory:dffd0000-dffdffff(prefetchable)

desktop:~$ ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:02:e3:24:51:b5
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:5 Base address:0xe000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:864 errors:0 dropped:0 overruns:0 frame:0
TX packets:864 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:66968 (66.9 KB) TX bytes:66968 (66.9 KB)
Many thanks.

---

### Post by yeats on 2011-06-19
How are you connecting to the web?  Through a modem or do you have a router of some sort in-between.  What happens when you do:

```
sudo dhclient eth0
```?

---

### Post by TheDoctorX on 2011-06-19
try to update yor network manager first ... some times happenz that network manager works bad ... for me was the same ... when i did the update it started workin' perfect ...

---

### Post by MacHackers on 2011-06-19
> **Clive Richardson said:**
> Have recently finished installing ubuntu 10.04.1 but am unable to establish an wired internet connection. I have made sure it is 'enabled' and have tried rebooting. I would be very grateful for any help.
Having seen other threads I have prepared the following information as each computer seems to have its individual problems. Comparing these results to those from my 8.04 version, I think the problem may be to do with RX & TX packets but have no idea what these are. 
I did post a similar message on the Installation Forum two days ago but haven't had any replies, so am hoping someone can help here.
desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:09.0 USB Controller: NEC Corporation USB (rev 41)
00:09.1 USB Controller: NEC Corporation USB (rev 41)
00:09.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
00:0c.0 Communication controller: Conexant Systems, Inc. HCF 56k Data/Fax/Voice Modem (rev 0
00:0d.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
00:0e.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 07)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS
desktop:~$ sudo lshw -C network
*-network
description: Ethernet interface
product: DP83815 (MacPhyter) Ethernet Controller
vendor: National Semiconductor Corporation
physical id: d
bus info: pci@0000:00:0d.0
logical name: eth0
version: 00
serial: 00:02:e3:24:51:b5
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half latency=64 link=no maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=10MB/s
resources: irq:5 ioport:d000(size=256) memory:dfffc000-dfffcfff memory:dffd0000-dffdffff(prefetchable)

desktop:~$ ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:02:e3:24:51:b5
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:5 Base address:0xe000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:864 errors:0 dropped:0 overruns:0 frame:0
TX packets:864 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:66968 (66.9 KB) TX bytes:66968 (66.9 KB)
Many thanks.
Firstly, Are you using Mac or PC? Secondly, up at the top of the menubar (notifications area, as so called by Ubuntu), right click the Wifi Bars and uncheck "Enable Networking". Reboot and See if that does it, If not, navigate to System > Administration > Hardware Drivers. Let it scan to see if there are any Hardware Drivers that need to be installed or updated. If that still doesn't get it, Navigate again to System > Administration > Package Manager. Type in your account password and let it scan for broken packages. If there are broken packages, see if you can 'fool' around with it and fix them. If you still have trouble, reply and I'll do the best I can. : )
 
Thanks!

---

### Post by Clive Richardson on 2011-06-19
Here it is:
desktop:~$ sudo dhclient eth0
DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:02:e3:24:51:b5
Sending on   LPF/eth0/00:02:e3:24:51:b5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by MacHackers on 2011-06-19
> **Clive Richardson said:**
> Have recently finished installing ubuntu 10.04.1 but am unable to establish an wired internet connection. I have made sure it is 'enabled' and have tried rebooting. I would be very grateful for any help.
Having seen other threads I have prepared the following information as each computer seems to have its individual problems. Comparing these results to those from my 8.04 version, I think the problem may be to do with RX & TX packets but have no idea what these are. 
I did post a similar message on the Installation Forum two days ago but haven't had any replies, so am hoping someone can help here.
desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:09.0 USB Controller: NEC Corporation USB (rev 41)
00:09.1 USB Controller: NEC Corporation USB (rev 41)
00:09.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
00:0c.0 Communication controller: Conexant Systems, Inc. HCF 56k Data/Fax/Voice Modem (rev 0
00:0d.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
00:0e.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 07)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS
desktop:~$ sudo lshw -C network
*-network
description: Ethernet interface
product: DP83815 (MacPhyter) Ethernet Controller
vendor: National Semiconductor Corporation
physical id: d
bus info: pci@0000:00:0d.0
logical name: eth0
version: 00
serial: 00:02:e3:24:51:b5
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half latency=64 link=no maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=10MB/s
resources: irq:5 ioport:d000(size=256) memory:dfffc000-dfffcfff memory:dffd0000-dffdffff(prefetchable)

desktop:~$ ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:02:e3:24:51:b5
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:5 Base address:0xe000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:864 errors:0 dropped:0 overruns:0 frame:0
TX packets:864 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:66968 (66.9 KB) TX bytes:66968 (66.9 KB)
Many thanks.
Hey, also, when you read my next post, this goes along with it.... I just forgot! : )
 
 
......... Try reinstalling Ubuntu from the Live CD, because Chances are that if you get an Internet Connection on the Live CD, and don't get it (with it being installed), something went wrong during the installation, or something 'messed' a package or file up in Ubuntu's HDD. If you can get a connection on the Live CD, try reinstalling Ubuntu.
 
Sorry for the Inconvience!

---

### Post by MacHackers on 2011-06-19
> **Clive Richardson said:**
> Here it is:
desktop:~$ sudo dhclient eth0
DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:02:e3:24:51:b5
Sending on   LPF/eth0/00:02:e3:24:51:b5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Uh Oh... Did you read my other posts?
 
If you can find some sort of connection, or by chance already have this.... Try
 
sudo iptraf
 
If you don't recall installing this or it says it's not installed, run
 
sudo apt-get install iptraf

then run, sudo apt-get update
 
Then, follow the on-screen instructions and run the **first** line (the first thing on the second part). Sorry, I don't know how'da explain it..

---

### Post by Clive Richardson on 2011-06-19
It's a PC year 2000.
Tried the 'enable networking' - no joy.
On Hardware it says 'No proprietary drivers in use on this system.
Package info.
1505 packages, 1295 Installed, 0 broken.

---

### Post by Clive Richardson on 2011-06-19
> **TheDoctorX said:**
> try to update yor network manager first ... some times happenz that network manager works bad ... for me was the same ... when i did the update it started workin' perfect ...
The Doctor X
How do you update a network manager? I can't see one.

---

### Post by MacHackers on 2011-06-19
The "Wireless Bars (also known as Wi-Fi)" are the Nework Connections Manager. Navigate to System > Administration > Network Connections. Add a Network and see if It'll connect... So, going back to your post earlier, are you using Wi-Fi or are you (trying) to use Ethernet? Plug in an Ethernet cable (one end to your computer and the other end to a port on the wall, a modem, or a router; if you are using the router, it is **"To other Computers" or "To Wired Devices" **or something similar) and type this into Terminal.....
 
**sudo ifconfig**
 
If it says "Command not Found".... Try this... (They both work, it is just that one of them is for the Windows Terminal and the other is for the Unix 'Ubunutu' Terminal. I just forget which ones are which time to time.) : )
 
**sudo ipconfig**
 
Post what it says for "eth0"....

---

### Post by Clive Richardson on 2011-06-19
:)SOLVED
Have re-installed and now working. Many thanks for all your help.

---

