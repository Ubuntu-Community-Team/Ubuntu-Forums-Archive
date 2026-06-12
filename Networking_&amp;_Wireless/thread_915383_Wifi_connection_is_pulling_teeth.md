---
title: "Wifi connection is pulling teeth"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by The Perennialist on 2008-09-09
I have dug through alot of posts trying to get my toshiba Satellite wifi connection to work. i would like to think it is something simple i am overlooking.... it is on Roaming and recognizes my signal but cannot connect. i have installed the wifi driver, fidgeted with the switch and thumbed other peoples problems for two days. 
my Network controller is the Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
-i believe i read on another post that this means i dont need any special driver but i am lost.
simple linksys router with no security..... 
am i missing anything?
thanks.

my specs:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

---

### Post by The Perennialist on 2008-09-09
if it makes a difference... i can patch out of my router and it connects. but when trying to connect to the wireless neither of the blue dots turns green. would the first one represent this computer or the detected network.?

i am thinking IP because i have had trouble with my desktop. but i cant get the ifconfig/release-renew commands to work

---

### Post by lisati on 2008-09-09
I, too, have one of the Toshiba Satellite range. Is your home network showing when you run the following from the terminal?
```
iwlist scan
```

---

### Post by The Perennialist on 2008-09-09
this is what i get.... 

valhallafields@Phoenix:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results





also i tried this but to no avail (i think):
valhallafields@Phoenix:~$ sudo dhclient wmaster0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

feels like im punching clowns in the dark .... at least its funn.

---

### Post by ba5ik7 on 2008-09-25
Man I tell you this OS could be so cool if everything worked. I've spent 3 days trying to get the wireless to work. Still nothing!!!! I've read and tried so much. But as it stands ubuntu doesn't support cs3 so I can't work on it and the wifi, mic, and web cam doesn't work so I can't use it for the web. Pulling teeth and losing hair is a great way to put it!!!

I got Wireless Network Drivers installed, and I install net5211 for the driver still nothing. So well I found another forum that said to install madwifi and run a whole bunch of commands. I don't think that it was install. I put it away at 3:00 last night. Still trying to get it to work...
OH..... I ran the same command 
```
iwlist scan
```
And came up with same output as you

I hope that someone out there can come with a solution ;)

My specs:
Toshiba P205D
AMD Turion64x2
Atheros 802.11 wireless LAN cards / Atheros AR5BXB63

Here a link for the madwifi solution [Atheros AR5BXB63 on Ubuntu Hardy Heron 8.04 with madwifi ]("http://brunoabinader.blogspot.com/2008/05/atheros-ar5bxb63-on-ubuntu-hardy-heron.html")

---

### Post by willca on 2008-09-26
If I read correctly, tried to do this

sudo iwlist wlan0 scan

And nothing came of it, ya?

if so, looks like your wifi driver is not loading correctly.

You might want to do ndiswrapper on this to get around it assuming you the windows driver somewhere.

---

### Post by ba5ik7 on 2008-09-26
> **willca said:**
> If I read correctly, tried to do this

sudo iwlist wlan0 scan

And nothing came of it, ya?

if so, looks like your wifi driver is not loading correctly.

You might want to do ndiswrapper on this to get around it assuming you the windows driver somewhere.

I tried that still nothing!!!!

---

