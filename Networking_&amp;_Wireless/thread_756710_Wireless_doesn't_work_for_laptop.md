---
title: "Wireless doesn't work for laptop"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by erikrutger on 2008-04-16
My laptop does scan wireless networks in the area, but I cannot join any of them; non-secured, that is. Also, I tried one secured network with login. Without result. This sucks, since the whole idea of this laptop was to being able to work online anywhere...

I have a laptop (Acer Travelmate 5310), with a Broadcom NetLink BCM5787M Gigabit Ethernet PCI Express wireless card. 

I have to say I'm still a newbie when it comes to Linux. But I already tried the following commands, inspired by similar posts:



erik@erik:~$ sudo lswh -C network
[sudo] password for erik:
sudo: lswh: command not found
erik@erik:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:16:d3:5d:58:3b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full firmware=5787m-v3.23 ip=10.0.0.80 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:be:9c:d3
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
erik@erik:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0C:F6:2F:FD:65
                    ESSID:"Kortmann"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=87/100  Signal level=-65 dBm  Noise level=-66 dBm
                    Extra: Last beacon: 172ms ago
          Cell 02 - Address: 00:11:D8:74:C0:4C
                    ESSID:"Verbeek_WL500g"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=84/100  Signal level=-71 dBm  Noise level=-70 dBm
                    Extra: Last beacon: 232ms ago
          Cell 03 - Address: 00:16:0A:09:66:32
                    ESSID:"Sweex LW050v2"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=80/100  Signal level=-75 dBm  Noise level=-70 dBm
                    Extra: Last beacon: 208ms ago
          Cell 04 - Address: 00:01:36:08:EC:47
                    ESSID:"CCW"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=89/100  Signal level=-61 dBm  Noise level=-70 dBm
                    Extra: Last beacon: 68ms ago
          Cell 05 - Address: 00:1C:10:AB:02:CF
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=81/100  Signal level=-74 dBm  Noise level=-70 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 176ms ago
          Cell 06 - Address: 00:0C:F6:2F:86:EF
                    ESSID:"Casema Internet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=77/100  Signal level=-80 dBm  Noise level=-70 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 68ms ago
          Cell 07 - Address: 00:01:E3:CD:3D:ED
                    ESSID:"SX552CD3DED"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=74/100  Signal level=-84 dBm  Noise level=-70 dBm
                    Extra: Last beacon: 92ms ago

erik@erik:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback







iface eth0 inet static
address 10.0.0.80
netmask 255.0.0.0
gateway 10.0.0.2

auto eth0

---

### Post by Gizim on 2008-04-16
I see the issue you have smiley faces in your commands!

---

### Post by erikrutger on 2008-04-16
haha. thanks...

---

