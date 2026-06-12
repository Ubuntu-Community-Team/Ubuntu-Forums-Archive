---
title: "Wireless troubles"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by Darth Muzzy on 2006-12-26
I am running Ubuntu 6.10 (Edgy).
I have a WMP54G v4 PCI wireless card.  I have used ndiswrapper to install a rt61 driver for it.
I am trying to connect to a 2wire wireless network.

sudo iwlist wlan0 scan returns

wlan0 Scan completed :
Cell 01 - Address: 00:0D:72:BA:A6:29
ESSID: "2WIRE940"
Mode:Master
Frequency:2.437 GHz
Encryption key:on
Extra:tsf=000000da48a3b2c4

it is set to DHCP.
I have entered the WEB password.


I still cannot connect, and when I use network tools to ping 2WIRE940, I am informed that that address cannot be found.

Any suggestions?

---

### Post by meng on 2006-12-26
Have you tried:
sudo dhclient wlan0

---

### Post by Floppyjoe on 2006-12-26
You need to add some info into the file /etc/network/interfaces:

Adding it to /etc/network/interfaces

/etc/network/interfaces is the file where your network interfaces are defined, eth0 being the standard wired interface. To make the wireless network come up when you start your computer put # in front of 'auto eth0' (to stop it automatically starting) and add something like the following lines.

auto wlan0
iface wlan0 inet dhcp
wireless-essid   MYNETWOTK
wireless-key     FEFEFEFEFE
wireless-channel 11
wireless-mode    managed

Where your wireless-mode might be master. The Channel and name of Essid need to be changed to your specs.

---

### Post by Darth Muzzy on 2006-12-26
sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:39:14:84:d6
Sending on   LPF/wlan0/00:18:39:14:84:d6
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Darth Muzzy on 2006-12-26
> **Floppyjoe said:**
> You need to add some info into the file /etc/network/interfaces:

Adding it to /etc/network/interfaces

/etc/network/interfaces is the file where your network interfaces are defined, eth0 being the standard wired interface. To make the wireless network come up when you start your computer put # in front of 'auto eth0' (to stop it automatically starting) and add something like the following lines.

auto wlan0
iface wlan0 inet dhcp
wireless-essid   MYNETWOTK
wireless-key     FEFEFEFEFE
wireless-channel 11
wireless-mode    managed

Where your wireless-mode might be master. The Channel and name of Essid need to be changed to your specs.



I moddified the /etc/network/interfaces file as suggested.  No apparent effect.

---

### Post by Darth Muzzy on 2006-12-26
could it be a problem with my drivers?  When I use "modprobe ndiswrapper" command I get a fatal error.  However, the "windows wireless driver" interface seems to work.

---

### Post by Floppyjoe on 2006-12-27
Can you post the contents of:

```
gedit /etc/network/interfaces
```

---

