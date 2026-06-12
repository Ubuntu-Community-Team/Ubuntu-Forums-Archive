---
title: "Wireless problem."
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by waytorun on 2007-03-01
I have 'Sens X10 plus' from Saumsung. It's a labtop PC.
It seems that the pro/wireless ipw2100 b3 is detected by the system but
I can't get online. I think driver is loaded as well. But [B]it's not associated with
the router(whatever assciation means in this context),[/B]


I ran 'iwconfig', 'iwlist eth1 scan' and 'lshw' and 'dhclient'
and following are results.



Result of 'iwlist eth1 scan'

'Cell 03 - Address: 00:13:10:A0:16:66
ESSID:"Danny"
Protocol:IEEE 802.11bg
Mode:Master
Channel:6
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 48 Mb/s; 54 Mb/s
Quality:84 Signal level:0 Noise level:0 Extra: Last beacon: 704ms ago




Result of ' iwconfig'

'lo no wireless extensions.

eth0 no wireless extensions.

eth1 unassociated ESSID:"danny"
Nickname:"ipw2100"
Mode:Managed Channel=0
Access Point: Not-Associated
Bit Rate=0 kb/s Tx-Power:16 dBm
Retry min limit:7 RTS thrff Fragment thrff
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extensions.



Result of ' lshp '


*-network:1
description: Wireless interface
product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
vendor: Iantel Corporation physical id: 7
bus info: pci@02:07.0 logical name: eth1 version: 04 serial: 00:0c:f1:2e:2c:65
width: 32 bits clock: 33MHz capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ipw2100 multicast=yes wirele


Result of 'dhclent'

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted



I've tried to install 'network manager' as lots of ppl seem to be using it,
but in add/remove section of Ubuntu it says it cannot be installed in my
computer type(i386).

Upper-right coner of panel, I see an network icon and I checked
it's 'about' and it's and app. called network monitor
I guess this is netwok manager like application.. it came with installation.

And I have WEP encryption on my router(linksys G)

I appreciate any help in advance.

I'm struggling with this for 48 hours straight.(I used linux for the first time
few days ago.).

Please help me out.

---

### Post by chili555 on 2007-03-01
Is this a typo, or are the essid's really different?```
Result of 'iwlist eth1 scan'

'Cell 03 - Address: 00:13:10:A0:16:66
ESSID:"Danny"
```
or, is it:```
Result of ' iwconfig'
eth1 unassociated ESSID:"danny"
```

The first thing I might suggest is sudo iwconfig eth1 essid Danny. Then I would do sudo dhclient eth1. If it works, I would sudo gedit  /etc/network/interfaces to change wireless-essid to Danny permanently.

Let us know!

---

### Post by waytorun on 2007-03-01
> **chili555 said:**
> Is this a typo, or are the essid's really different?```
Result of 'iwlist eth1 scan'

'Cell 03 - Address: 00:13:10:A0:16:66
ESSID:"Danny"
```
or, is it:```
Result of ' iwconfig'
eth1 unassociated ESSID:"danny"
```

The first thing I might suggest is sudo iwconfig eth1 essid Danny. Then I would do sudo dhclient eth1. If it works, I would sudo gedit  /etc/network/interfaces to change wireless-essid to Danny permanently.

Let us know!


Thank you for reply. REALLY appreciate it.


To answer your question, it's not a typo. One says Danny, and the other says

danny.

I've ran ' sudo  iwconfig eth1 Danny ' and following is result.

(Doesn't look like it worked, at least the command ran anyway)


danny@danny-laptop:~$ sudo iwconfig eth1 essid Danny
Password:
danny@danny-laptop:~$ sudo dhdclient eth1
sudo: dhdclient: command not found
danny@danny-laptop:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0c:f1:2e:2c:65
Sending on   LPF/eth1/00:0c:f1:2e:2c:65
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


and the content of /etc/network/interfaces is following.

auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


Shouldn't there be eth1 info here?

---

