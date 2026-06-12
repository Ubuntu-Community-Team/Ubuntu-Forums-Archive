---
title: "driver installed, can see network but no connection"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by alanmzifa on 2006-08-28
Hi, I've be trying off and on over the last few days to get a wireless USB adapter connected. It's a Netgear WG121. I've read loads of threads and tried a lot of things and Network Manager showed network and signal strength for a few seconds (after I'd blacklisted islsm, I picked that up on another thread, for better or worse) but now doesn't show at all. In fact the Network Manager applet doesn't show now. I also don't seem able to edit the blacklist again or interfaces in modprobe.d (don't have permission).

Here's some terminal output....*I'm new to Linux* and dual booting with XP but I'd switch if I could get the network up.

***Thanks in advance. Anyone have any ideas or want to lend a hand?***

> monty@monty-desktop:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:11:F5:F8:53:E8
                    ESSID:"BTVOYAGER2091-E8"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:0/100  Signal level:-74 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1
          Cell 02 - Address: 00:0C:76:CA:1B:A7
                    ESSID:"access_point"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-60 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=3
          Cell 03 - Address: 00:09:5B:CD:08:38
                    ESSID:"W office"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:0/100  Signal level:-44 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=2

and

> monty@monty-desktop:~$ sudo ndiswrapper -l
Installed ndis drivers:
netwg121                driver present, hardware present

---

### Post by alanmzifa on 2006-08-28
_**small update**_

Uninstalled network manager and installed wifi-radar as i suspected network manager may have been causing problems (hunch rather than logic). So the driver was set up with ndiswrapper and lslsm was blacklisted. Then picked up network with wifi-radar.

Am able to get a conection now using wifi-radar but only if I disable security! 

**Does anyone have any suggestions as to how I can add WEP to this?**

Here's a screenshot of where I am now. Sorry, not sure how to resize in gimp.

---

