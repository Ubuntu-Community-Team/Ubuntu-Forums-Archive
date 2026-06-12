---
title: "Can't get my wireless to work."
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by waytorun on 2007-03-01
Hi, I just experienced lunux for the first time today, so please forgive me
for any 'noobness'.


I have 'Sens X10 plus' from Saumsung. It's a labtop PC.
It seems that the pro/wireless ipw2100 b3 is detected by the system but
I can't get online. I think driver is loaded as well. [B][I]But it's not associated with
the router(whatever assciation means in this context),[/I][/B]

I was reading thru some stuff about ubuntu
and came upon couple of commands.

I ran 'iwconfig', 'iwlist eth1 scan' and 'lshw',
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

eth1 ***unassociated ***ESSID:"danny"
Nickname:"ipw2100"
Mode:Managed Channel=0
Access Point: ***Not-Associated***
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






I've tried to install 'network manager' as lots of ppl seem to be using it,
but in add/remove section of Ubuntu it says it cannot be installed in my
computer type(i386).

but mine is just regular labtop PC with intel pro/wireless chip(centrino)

Upper-right coner of panel, I see an network icon and I checked

it's 'about' and it's called network monitor
I guess this is netwok manager like application.. it came with installation.

And I have WEP encryption on my router(linksys G)


I appreciate any help in advance.

(Going little crazy here to tell you the truth, but enjoyin ubuntu at the
same time ! )

---

### Post by nachotronics on 2007-03-02
Have you followed every step?? you might want to try installing network-manager-gnome following **[this howto]("https://help.ubuntu.com/community/WifiDocs/NetworkManager?highlight=%28network%29%7C%28manager%29")**. This utility helps you set up WEP or WPA secured networks.

Hope this helps.

---

### Post by chili555 on 2007-03-05
Danny is not the same as danny. One or the other must change before your wireless card will **associate** (connect, for the plain-spoken among us).

I would also double-check my WEP configuration. Here is a guide that may help: [http://www.ubuntuforums.org/showthread.php?t=172810&page=2](http://www.ubuntuforums.org/showthread.php?t=172810&page=2)

---

