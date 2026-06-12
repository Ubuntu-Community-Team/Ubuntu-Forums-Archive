---
title: "Wireless - connected woth 99 % strength but can't go online"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by Howl01 on 2007-10-26
I have a Dell 6400 n notebook with the PRO/Wireless 3945ABG wireless card

I am able 2connect 2my router wirelessly, and it shows that I have a signal strength of 99 % when i hover over the blue bars in the top right...but I cannot go online, it jus says that the page cannot be displayed

Any ideas why this is?

Here's some additional info:


howl@dell:~$ lshw
*-network
description: Wireless interface
product: PRO/Wireless 3945ABG Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0b:00.0
logical name: eth1
version: 02
serial: 00:1b:77:d2:b8:0b
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 multicast=yes wireless=unassociated
resources: iomemory:efdff000-efdfffff irq:16



howl@dell:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

eth1 unassociated ESSIDff/any
Mode:Managed Frequency=nan kHz Access Point: Not-Associated
Bit Rate:0 kb/s Tx-Power:16 dBm
Retry limit:15 RTS thrff Fragment thrff
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:96 Missed beacon:0



howl@dell:~$ sudo iwlist scan
Password:
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

eth1 Scan completed :
Cell 01 - Address: 00:0F:B5:CE:F5:9E
ESSID:"NETGEAR"
Protocol:IEEE 802.11bg
Mode:Master
Channel:11
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
36 Mb/s; 48 Mb/s; 54 Mb/s
Quality=99/100 Signal level=-22 dBm Noise level=-22 dBm
Extra: Last beacon: 376ms ago

---

### Post by bswilson on 2007-10-26
It does appear your Wireless card is configured correctly.  But can you ping your default gateway?  If so, can you ping various hosts such as [www.yahoo.com?](www.yahoo.com?)

---

### Post by Howl01 on 2007-10-26
Results:

howl@dell:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=255 time=1.06 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=255 time=0.752 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=255 time=0.754 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=255 time=0.732 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=255 time=0.752 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=255 time=0.738 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=255 time=0.755 ms
64 bytes from 192.168.0.1: icmp_seq=8 ttl=255 time=0.762 ms
64 bytes from 192.168.0.1: icmp_seq=9 ttl=255 time=0.735 ms


howl@dell:~$ ping [www.google.com](www.google.com) -a
PING [www.l.google.com](www.l.google.com) (64.233.183.147) 56(84) bytes of data.
64 bytes from nf-in-f147.google.com (64.233.183.147): icmp_seq=1 ttl=237 time=24.6 ms
64 bytes from nf-in-f147.google.com (64.233.183.147): icmp_seq=2 ttl=237 time=24.9 ms
64 bytes from nf-in-f147.google.com (64.233.183.147): icmp_seq=3 ttl=237 time=24.7 ms
64 bytes from nf-in-f147.google.com (64.233.183.147): icmp_seq=4 ttl=237 time=25.0 ms
64 bytes from nf-in-f147.google.com (64.233.183.147): icmp_seq=5 ttl=237 time=24.2 ms

---

