---
title: "AR9285 cannot connect to specific network using lubuntu 15.10 (driver ath9k)"
date: 2016-03-13
forum: Networking &amp; Wireless
---

### Post by georges4 on 2016-03-13
Hi there :)

This is my first post, but I'll try to make it intelligent.

Here is my problem :

I have a dual boot on a Packard Bell laptop (DOT_SE-310FR). Lubuntu can't connect to my home network (open ssid, wpa security) while windows xp can do it with no problem. After prompting my password, it'll try connecting for 30sec and then prompt again asking my password. I also occasionally use Puppy Linux (Lucid 5.28), and when running on this machine I also experience the same problem.
Other devices running lubuntu or other OS have had no problems connecting to this network.

I've scouted on the forums and thought that the problem came from the fact that my network is using a N connection not supported by my lubuntu driver (ath9k). I tried on another N wireless network to check but it worked fine.

I'm really clueless !

Here is the main info from my wireless-info script. The rest is attached in an .tar.gz file

```
lspci #############################

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
    Subsystem: Acer Incorporated [ALI] Device [1025:034a]
    Kernel driver in use: atl1c

02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e016]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 001 Device 002: ID 04f2:b209 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

#####
```

Thanks a lot !
PS : the network showing on my wireless info file is not the one I'm having trouble with, it's my phone's 3G connection.

---

### Post by jeremy31 on 2016-03-13
I would start by changing encryption on the wifi router to WPA2 only with no WEP or TKIP and change it from auto channel to channel 13, save the settings and reboot the router.

It was on a crowded channel and Linux distros don't work well with TKIP

---

### Post by georges4 on 2016-03-13
> **jeremy31 said:**
> I would start by changing encryption on the wifi router to WPA2 only with no WEP or TKIP and change it from auto channel to channel 13, save the settings and reboot the router.

It was on a crowded channel and Linux distros don't work well with TKIP

Thanks Jeremy.

The network in my wireless info file is not the  one I'm having problems with (my home network), but the one from my  phone's 3G instead.

I am not sure how I can get the info from the  network I'm having trouble with to show since I can't connect to it  (well I can with XP, but I don't know if that can help).

---

### Post by jeremy31 on 2016-03-13
The wifi you are connected to in the script is ```
Cell 01 - Address: <MAC 'lovephone' [AC1]>                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-23 dBm  
                    Encryption key:on
                    ESSID:"lovephone"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000004cf3020b
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
```

And I imagine the wifi you are having issues with is ```
Cell 17 - Address: <MAC 'lovebox' [AC17]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"lovebox"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006bf54648aa
                    Extra: Last beacon: 376ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
```

The phone is using WPA2 with AES(CCMP) encryption only, were your network is using WPA with mixed mode encryption and your network on channel 11 with 12 other wifi access points
```
Channel occupancy:


      6   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      3   APs on   Frequency:2.422 GHz (Channel 3)
      7   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.447 GHz (Channel 8)
      4   APs on   Frequency:2.452 GHz (Channel 9)
      13   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.472 GHz (Channel 13)

```

---

### Post by georges4 on 2016-03-13
Oooooh.

Thanks a lot, I'm checking this and will let you know if it worked !

---

### Post by georges4 on 2016-03-13
Ok so I managed to connect, but only after changing to a WEP security.

> **jeremy31 said:**
> I would start by changing encryption on the wifi router to WPA2 only with no WEP or TKIP and change it from auto channel to channel 13, save the settings and reboot the router.

I tried to do that through the interface provided by my internet provider in my online account management. I couldn't get it to change to WPA2, but only could change to WPA (version 1) with no TKIP, and it still couldn't connect.

I also changed the channel on two different, less crowded channels but that didn't do the trick either.

I then thought of trying to change to WEP security just to try and that way I am able to connect.

Any idea why WPA won't work ? I sorta liked my password and it won't fit WEP standards :D

Here's the exact "no TKIP" setting I tried (which didn't work) :
```
Cell 04 - Address: <MAC 'lovebox' [AC4]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"lovebox"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000004d84adad
                    Extra: Last beacon: 764ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
```

---

### Post by jeremy31 on 2016-03-13
Strange that it worked with WEP and not WPA.  I would still prefer WPA2 as the security is harder to break

---

