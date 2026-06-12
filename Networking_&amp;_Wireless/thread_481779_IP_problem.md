---
title: "IP problem"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by dbaile10 on 2007-06-22
Ok after hours of work i've finally got my wireless card up and running, network detected, and everything looking how it should be, except the fact that for some reason when i try to connect to the network, i cannot aquire an ip address. Has anyone had this problem before or know how i could go about fixing it. 

Thank you.

---

### Post by chippy99 on 2007-06-22
Have you enabled DHCP on your router and in your network settings.

What happens if you set a static IP address (in same IP subnet as your router) on your computer ?

---

### Post by dbaile10 on 2007-06-22
I've tried both multiple times to no avail, i've also tried that with different network managers, and nothign seems to be working

---

### Post by kevdog on 2007-06-23
What happens with
iwlist (interface name) scanning

Example
iwlist eth0 scanning
iwlist wlan0 scanning

---

### Post by dbaile10 on 2007-06-23
This is what i get back for wlan0

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:91:63:5F
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Quality=49/100  Signal level=29/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:09:5B:CB:62:78
                    ESSID:"NETGEAR"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/100  Signal level=29/100  Noise level=0/100
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
          Cell 03 - Address: 00:0F:B5:6C:18:FA
                    ESSID:"Tascware"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/100  Signal level=8/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:14:BF:33:41:AA
                    ESSID:"Hughes"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/100  Signal level=4/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

it says that eth0 doesnt support scanning

as far as i know this is a list of the different networks available, mine is linksys, and every time i try to connect, it says its connected, however i cant get any web pages up or access the router

---

