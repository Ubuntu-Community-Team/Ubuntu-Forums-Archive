---
title: "Wireless keeps dropping connection"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by Merlene on 2007-02-05
Hi there,

I'm using Ubuntu 6.06 (after several failed attempts to use Edgy with my wireless card + ndiswrapper) and a d-link dwl-g132 usb wireless adapter. I can connect (am currently posting) but my problem is that my connection seems to drop off frequently. Sometimes it'll stay connected for hours and other times I'm lucky for a connection to hold longer than 5 or 10 minutes. 

Network manager shoes that it's connected but I'm getting nothing and I'll have to force it to reconnect to get things working again. Very frustrating.

I do not have the same problem when using XP (I'm dual booting on 2 partitions), my wireless will stay connected for days on XP.

Anything I"m missing here?

---

### Post by Demodog on 2007-02-06
Im having the same problem with mine. I was asuming it was because the network card dont really is supported in linux but I don´t know for sure.

---

### Post by gradedcheese on 2007-02-06
If the card seems to still have a signal when the connection seems lost, I would check to see if it's not perhaps a different problem.  For example, can you still ping your router?  For example:

ping 192.168.1.1

if so, then perhaps it's a DNS problem and not a WiFi issue.  Also, see that the configuration for this card makes sense.  For example, if its named eth1:

ifconfig eth1
iwconfig eth1

The first should tell you your IP address, netmask, and so on.  The second will give you the current wireless configuration (SSID, whether you're associated, etc).  Check especially whether you're associated, if you are not, try re-associating.  Finally, if everything looks good but doesn't work, perhaps try asking for another IP address from the DHCP server (assuming you're using DHCP), for eth1 for example:

sudo dhclient eth1

---

### Post by Merlene on 2007-02-06
Ok so I did the ifconfig and iwconfig with these results:

$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:13:46:E5:38:DA
          inet addr:192.168.2.11  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:fee5:38da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1482647 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1392094 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1158541698 (1.0 GiB)  TX bytes:903839373 (861.9 MiB)

:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"PaYNTeR"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:A3:1D:C2:99
          Bit Rate:54 Mb/s
          Link Quality:0/100  Signal level:-63 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I'm not really sure what's meant by associated or what I need to do next?

~$ sudo dhclient wlan0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:13:46:e5:38:da
Sending on   LPF/wlan0/00:13:46:e5:38:da
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.11 -- renewal in 117527 seconds.


I did the sudo dhclient wlan0 with the above result...

---

### Post by Hanzerik on 2007-02-06
What type of CPU are you using and what kernel are you using?

I have a similar issue on my laptop (Intel Core Duo) using SMP (686) kernels. So I instead I use a 486 kernel and have no more issues.

Seem that when I use a SMP kernel, and the NIC is not stressed it works fine, but once the connection is stressed and the other CPU starts getting used my wireless card has an IRQ conflict, and the kernel shuts the IRQ down, disabling the NIC.

---

### Post by Hanzerik on 2007-02-06
See if these are the type of symptoms you are getting:

[http://www.google.com/search?q=Nvidia+ndiswrapper+irq+conflicts](http://www.google.com/search?q=Nvidia+ndiswrapper+irq+conflicts)

Just FYI, My Laptop has these specs:
Dell Inspiron 1705
Intel CoreDuo T2500
Nvidia Geforce 7900GS
Broadcom 1390 chipset

Ndiswrapper is required for wireless.
Currently using Debian Etch and the 2.6.18.3-486 kernel with no issues, the 686 would give me Irq conflicts and makes networking stop.

---

### Post by Merlene on 2007-02-06
CPU  - not sure brand but it's a 3.0 ghz
kernel - Ubuntu, kernel 2.6.15-27-386

I'm not using a nvidia card

I have to use ndiswrapper for the wireless to work

---

### Post by Merlene on 2007-02-07
I'm still hoping someone can offer me some advice on how to fix this.

I've noticed over the last day or so that many times when I notice the connection has been dropped there's one or more wireless networks (other than my own) showing up or disappearing. So what I suspect is that network manager (it's the kde version knetworkmanager) is stalling whenever a wireless network appears or disappears.

Anyone know of a way I can tell knetworkmanager to ignore all other wireless networks other than my own????????

---

### Post by Nakkis on 2007-02-07
See my post here and try if it helps. :) 

[http://www.ubuntuforums.org/showthread.php?t=355523](http://www.ubuntuforums.org/showthread.php?t=355523)

---

