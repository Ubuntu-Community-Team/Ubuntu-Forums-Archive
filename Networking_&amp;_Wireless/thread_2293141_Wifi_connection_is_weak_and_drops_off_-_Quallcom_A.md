---
title: "Wifi connection is weak and drops off - Quallcom Atheros AR9485 on Asus S400CA"
date: 2015-09-03
forum: Networking &amp; Wireless
---

### Post by Matematik on 2015-09-03
Wifi connection on my Asus S400 with Quallcom Atheros AR9485 wifi card is very weak. When I try to browse the web my wifi connection often drops off. On other laptops in my house I have full-strength connection, but this laptop is only showing 2 out of 5 bars. Sometimes the wifi icon shows that I'm connected, but pings don't go through and web pages are not accessible.

This problem was happening to me on Ubuntu 12.04, 14.04, and now 15.04. It became very troublesome when I switched from an old Netgear wireless router (which died) to DLink DIR-601.

Should I change wifi card or there's a problem with my config? Should I report it as a bug on Launchpad? Any suggestions on tackling this problem are very much appreciated!

I'm  attaching dmesg and /var/log/syslog logs captured around the time when  problem occurred

--------------------------------------

When I have my wireless connection dropped I'm usually trying to bring it back up with the following script:

```

#!/bin/bash
set -x
sudo service network-manager stop
sudo rmmod -v ath9k
sudo modprobe -v ath9k
sudo service network-manager start

```

Here's some more system information

[FONT=fixedsys]**$ sudo iwlist wlan0 scan**
wlan0     Scan completed :
          Cell 01 - Address: 00:26:5A:F7:AC:EE
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"Kolobok"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003ec8a287c
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 00074B6F6C6F626F6B
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555349010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD9E0050F204104A0001101044000102103B000103104700100000000000001000000000265AF7ACEE10210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363031104200046E6F6E651054000800060050F204000110110016442D4C696E6B2053797374656D73204449522D363031100800020086103C000103104900140024E26002000101600000020001600100020001
                    IE: Unknown: DD050050F20500

**$ sudo lshw -C network**
  *-network               
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: dc:85:de:a2:2b:d6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.19.0-26-generic firmware=N/A ip=192.168.0.106 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f7d00000-f7d7ffff memory:f7d80000-f7d8ffff
  *-network
       description: Ethernet interface
       product: AR8161 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 50:46:5d:45:94:9c
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
       resources: irq:31 memory:f7c00000-f7c3ffff ioport:e000(size=128)[/FONT]

---

