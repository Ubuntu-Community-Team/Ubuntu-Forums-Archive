---
title: "Wireless not working on 6.10"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by ichbinbored on 2007-10-26
I've got Ubuntu Server with the LAMP stack running on a PC, which is connected wirelessly to my router with a Linksys WMP54G card. I originally had 6.06 running on there and it was working fine, with the card appearing as ra0.

However, I installed the mediawiki package and wanted to put Firefox on there so I could test it out (as elinks hurts my eyes ;)), so I installed the ubuntu-desktop package. It all worked fine, and then I updated to 6.10. This took hours as it had to download all of the updates to all of the packages that ubuntu-desktop brought in, so I decided to get rid of it again so updating would be quicker. I restarted, and tried to remove ubuntu-desktop using

```
sudo apt-get remove ubuntu-desktop
```

However, this only removed the virtual package. I tried to install it again so that I could try autoremove and --purge, but as it didn't add any new packages this time then none were removed. Now whenever I try to install ubuntu-desktop to try something else it wants to download a load of extra packages.

After I had upgraded, the wireless card came up in the Device Manager as two separate entries under one device. Instead of ra0 it came up as wmaster0 and wlan0. wlan0 came up as a network interface, and wmaster0 came up as an unknown device. I tried configuring wlan0 using

```
iwconfig essid "myessid" key mykey mode Managed
```

but it came up with this when I ran dhclient:

```
michael@LULZserver:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: Input/output error
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:f8:2a:3c:a4
Sending on   LPF/wlan0/00:18:f8:2a:3c:a4
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

As a result, I can't install ubuntu-desktop again as it's missing a load of packages which I can't download.

Any ideas on how I can get wireless working on Edgy and get rid of ubuntu-desktop once and for all? I don't mind keeping ubuntu-desktop if I have to, but the internet's pretty essential.

Thanks in advance :)

---

