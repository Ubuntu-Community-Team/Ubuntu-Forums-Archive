---
title: "kubuntu network problems"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by tdragosh on 2007-04-07
I'm using Kubuntu and Windows XP on the same computer. I had a problem with my Windows and I formatted that partition. I didn't know how to replace only the GRUB and I installed Kubuntu over the old one. The thing is that now I can't access internet at all on Kubuntu... Not even from the live CD. I'm not too good on Linux so I can't figure out what's going on...
Please help...:(

---

### Post by caffienefree on 2007-04-07
Could you please supply details, such as your network card, Kubuntu version, connection details?

EDIT: Oh, now I see, Kubuntu 6.06.

---

### Post by tdragosh on 2007-04-07
My  network card is Realtek RTL8168/8111 PCI-E Gigabit.

The thing is that the first time when I installed kubuntu it worked perfect... I didn't have to configure anything. After I formated the partition even the Live CD was not able to connect to the Internet and could not install the security updates. 

My /etc/networks/interfaces looks normal... Just it has like 5 interfaces... Is this OK?

I got an ifconfig result here:

root@dragosh-desktop:~# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:13:8F:D9:B3:A5
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2702 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:175472 (171.3 KiB)  TX bytes:2394 (2.3 KiB)
          Interrupt:185 Base address:0xe800


and a dhclient...
root@dragosh-desktop:~# dhclient eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:13:8f:d9:b3:a5
Sending on   LPF/eth0/00:13:8f:d9:b3:a5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

