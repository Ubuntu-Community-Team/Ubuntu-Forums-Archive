---
title: "Internet works but top right icon says 'No network connection'"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by jrpfinch on 2007-05-09
I am afraid I am fairly new at Linux/Ubuntu.

I managed to get Firefox to work fine with my Intel EtherExpress 10/100 ISA card by adding the following to /etc/modules:

eepro autodetect=1

However, the icon in the top right corner of my desktop displays an ! and says 'No network connection'.  ifconfig -a returns:

eth0      Link encap:Ethernet  HWaddr 00:AA:00:C9:08:40  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2aa:ff:fec9:840/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:319 errors:0 dropped:0 overruns:0 frame:0
          TX packets:358 errors:0 dropped:0 overruns:0 carrier:1
          collisions:3 txqueuelen:1000 
          RX bytes:319905 (312.4 KiB)  TX bytes:74221 (72.4 KiB)
          Interrupt:3 Base address:0x210 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

I am running Feisty Fawn and /etc/network/interfaces contains:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


Is this anything I should worry about?  Even if it's just the network icon that's broken, I'd quite like to fix it because it's annoying!  Any help appreciated.

Cheers

Jon

---

