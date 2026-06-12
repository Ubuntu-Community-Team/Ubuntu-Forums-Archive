---
title: "[SOLVED] Internet connection problems, I neeeeed Heeeelp"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by beidache on 2008-10-21
Hello I have problems to connect my computer dell Latitude d620, this is the information my computer gave to me:

petacho@Conexionchina:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
petacho@Conexionchina:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:230  Noise level:165
          Rx invalid nwid:0  invalid crypt:38  invalid misc:0

petacho@Conexionchina:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1b:fc:00:87:b3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:c6:6c:bb
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5752-v3.19 ip=192.168.1.102 latency=0 module=tg3 multicast=yes
petacho@Conexionchina:~$ 

Someone can help me? Im using Ubuntu 8.4

---

### Post by beidache on 2008-10-21
I just saw this:
 description: Wireless interface
 width: 32 bits

 description: Ethernet interface
 width: 64 bits

I dont know if that is part of the problem

---

### Post by cariboo on 2008-10-22
It looks like your wired nic is setup, have you tried in a Applications--Accessories-->Terminal:

```
sudo dhclient eth0
```

Could you also tell us how your connecting to the internet?

Jim

---

### Post by beidache on 2008-10-22
Hey Jim thanks for your answer I wrote sudo dhclient eth0 and this what i had:

petacho@Conexionchina:~$ sudo dhclient eth0
[sudo] password for petacho: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:18:8b:c6:6c:bb
Sending on   LPF/eth0/00:18:8b:c6:6c:bb
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.1.102 from 192.168.1.1
DHCPREQUEST of 192.168.1.102 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.102 from 192.168.1.1
bound to 192.168.1.102 -- renewal in 3072 seconds.

And then I wrote iwconfig and this is what i got:

petacho@Conexionchina:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:228  Noise level:165
          Rx invalid nwid:0  invalid crypt:2601  invalid misc:0

petacho@Conexionchina:~$ 

Thats mean still with out work

Im connected via ethernet

---

### Post by beidache on 2008-10-23
Problem solved this is what I put at the end

You also need to blacklist b43 and ssb:
Code:

echo -e 'blacklist b43\nblacklist ssb' | sudo tee -a /etc/modprobe.d/blacklist

After that, to test your wireless:
Code:

sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx
sudo modprobe ndiswrapper
sudo iwlist scan

Hope that helps.
Ayuthia

---

