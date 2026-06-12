---
title: "Reinstalled ubuntu---More wireless probs"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by 98GreenGT on 2007-09-11
Alright i did a clean install of ubuntu and got wireless up and working pretty fast, only thing being that it just will not connect to any network other than my own network with WPA.

---

### Post by 98GreenGT on 2007-09-11
lshw -C network

*-network               
       description: Wireless interface
       product: BCM4310 UART
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@01:00.0
       logical name: wlan0
       version: 01
       serial: 00:1a:73:3a:c0:82
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic ip=192.168.1.102 latency=0 wireless=IEEE 802.11b/g
       resources: iomemory:c3000000-c3003fff irq:22
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wlan1
       serial: 00:0a:e9:09:1d:62
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
------------------------------------------------------------
iwlist scan

 Scan completed :
          Cell 01 - Address: 00:18:39:EE:0E:30
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:3
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=89/100  Signal level=-63 dBm  Noise level=-68 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 524ms ago
          Cell 02 - Address: 00:1C:10:08:75:8A
                    ESSID:"GETOFFMYLINKSYS"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=98/100  Signal level=-41 dBm  Noise level=-69 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 84ms ago

GETOFFMYLINKSYS is mine
---------------------------------------------------------
Not sure what else i can give you that will help

Also you'll notice something about wlan1 or eth1 and thats a ashton digital WRUB-2011i usb wireless stick that i cant get to work either

---

### Post by 98GreenGT on 2007-09-12
Still isnt connecting to any other networks, im at school now and forced to use vista because it wont connect to the universities wifi.  It is scanning/finding all wireless networks but its just refusing to connect to any of them

---

### Post by 98GreenGT on 2007-09-14
no help?  Its still acting pretty odd around the university network..it will connect now but its extremely slow

---

