---
title: "Wireless network intermittently disconnecting"
date: 2020-12-10
forum: Networking &amp; Wireless
---

### Post by alecjw on 2020-12-10
I've been struggling with a problem with my wifi disconnecting recently. I think I've finally solved it so I thought I'd share in case anyone else is having the same problem.
This may be relevant to you if you have a dual-band router and you use networkmanager.

I'm using xubuntu with NetworkManager. Most of the time, my wifi is perfectly fine but occasionally it disconnects and pops up asking for my password again:
[ATTACH=CONFIG]287522[/ATTACH]
It happens randomly. Sometimes it goes a few hours without doing it and sometimes it happens a few times within a couple of minutes of each other.

dmesg gives me this output when it happens:
```
[ 5844.315345] wlo1: disconnect from AP 04:81:9b:5a:e6:72 for new auth to 04:81:9b:5a:e6:75
[ 5844.320044] wlo1: authenticate with 04:81:9b:5a:e6:75
[ 5844.323657] wlo1: send auth to 04:81:9b:5a:e6:75 (try 1/3)
[ 5844.351707] wlo1: authenticated
[ 5844.353596] wlo1: associate with 04:81:9b:5a:e6:75 (try 1/3)
[ 5844.354628] wlo1: RX ReassocResp from 04:81:9b:5a:e6:75 (capab=0x1011 status=0 aid=2)
[ 5844.356499] wlo1: associated
[ 5844.372978] wlo1: deauthenticating from 04:81:9b:5a:e6:75 by local choice (Reason: 1=UNSPECIFIED)

```

Googling the "deauthenticating by local choice" message I found that it might be due to a [conflct between NetworkManager and wpa_supplicant]("https://bbs.archlinux.org/viewtopic.php?id=233365"). Disabling wpa_supplicant didn't fix it though.

Another lead I found was that it might be related to my [region not being set]("https://superuser.com/questions/974017/ubuntu-wlan0-authenticates-and-then-drops"). I set it to UK but still had the same problem.

I think I've finally found the solution. The answer is in the first line of the dmesg output:
```
[ 5844.315345] wlo1: disconnect from AP 04:81:9b:5a:e6:72 for new auth to 04:81:9b:5a:e6:75
```

From an iwlist scan, you can see that these BSSIDs correspond to the 2.4GHz and 5GHz channels from my dual band router:
```
alec@rhea:~$ sudo iwlist scan
[sudo] password for alec: 
lo        Interface doesn't support scanning.

wlo1      Scan completed :
          Cell 01 - Address: 04:81:9B:5A:E6:75
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Not free advertising for my ISP"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009d28c0777e
                    Extra: Last beacon: 148ms ago
                    IE: Unknown: 001F4E6F742066726565206164766572746973696E6720666F72206D7920495350
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 07344742202401172801172C01173001173401173801173C011740011764011E68011E6C011E70011E74011E84011E88011E8C011E00
                    IE: Unknown: 200100
                    IE: Unknown: 23021400
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0B050200070000
                    IE: Unknown: 420100
                    IE: Unknown: 46057208010000
                    IE: Unknown: 2D1AEF0117FFFFFFFF00000000000000000000000000000000000000
                    IE: Unknown: 3D1624050400000000000000000000000000000000000000
                    IE: Unknown: 7F080400080000000040
                    IE: Unknown: BF0CB269830FAAFF0000AAFF0000
                    IE: Unknown: C005012A000000
                    IE: Unknown: C30402020202
                    IE: Unknown: DD0500904C0417
                    IE: Unknown: DD090010180202001C0000
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 02 - Address: 04:81:9B:5A:E6:72
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"Not free advertising for my ISP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009d2696790e
                    Extra: Last beacon: 3864ms ago
                    IE: Unknown: 001F4E6F742066726565206164766572746973696E6720666F72206D7920495350
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C121860
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0B050000420000
                    IE: Unknown: 420100
                    IE: Unknown: 46057208010000
                    IE: Unknown: 2D1AAD0117FFFFFFFF00000000000000000000000000000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: 7F080400080000000040
                    IE: Unknown: DD1E00904C0400BF0CB2018003AAFF0000AAFF0000C005000B000000C3020002
                    IE: Unknown: DD090010180200001C0000
                    IE: Unknown: DD180050F20201018C0003A4000027A4000042435E0062322F00

```

So it seems like it's trying to hop between bands. Apparently this is related to a "roaming" feature: it's supposed to allow me to transparently hop between different access points on the same network. I suppose the primary application is for things like linked routers in an a large office, conference centre, university building etc.

Apparently, [a change about a year ago]("https://www.phoronix.com/scan.php?page=news_item&px=NetworkManager-Roam-Aggressive") changed the threshold for switching between access points from -80dBm to -70dBm. And in the iwlist scan output above, you can see that my 5GHz network strength is -67dBm. So it seems hardly surprising that it will sometimes drop below that level and trigger roaming to try and connect to 2.4GHz instead!
I guess this shouldn't cause a problem but [according to archwiki]("https://wiki.archlinux.org/index.php/NetworkManager#Regular_network_disconnects,_latency_and_lost_packets_(WiFi)"), it can cause problems with some buggy wifi drivers. I wouldn't be surprised if a buggy router could also be part of the problem. For what it's worth, my wifi card is:
```
5c:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)
```
And my router is a sky SR203 hub with firmware version 5.11.1993.R.

So the possible solutions seem to be:
[LIST=1]
[*]Switch to a patched version of NetworkManager with scanning disabled, as per the archwiki link
[*]Disable one of the bands on my router, or change the ESSIDs to be different
[*]Set NetworkManager to only connect to the BSSID of my 5GHz network
[*]
[/LIST]

Option 1 isn't really an option because I don't want to have to compile my own version of NetworkManager and keep it updated myself. If I was using gentoo I might have considered that.
Option 2 is a possibility. Legacy devices still exist so I can't disable 2.4GHz. I have some around my home and mostly they're awkward to change wireless settings on (games consoles etc) so if I change anything it will be the 5GHz network. As much as 5GHz is technically superior, I've never really noticed much benefit (my internet is only 63Mbit/s anyway) so I'd probably just disable 5GHz. Although if I still wanted some devices to connect to 5GHz, I could still keep it active but with a different ESSID.
Option 3 though is what I went for: I added a new network in NetworkManager with a fixed BSSID. I also gave it a higher priority than the existing network so that NetworkManager would connect to the fixed BSSID connection over the "roaming" one.
[ATTACH=CONFIG]287523[/ATTACH][ATTACH=CONFIG]287524[/ATTACH]
Why did I not delete or overwrite the "roaming" one? Well, I like the convenience of having the same ESSID and security key for multiple networks. Eg my phone's tethering hotspot has the same ESSID to save me configuring my devices for two different networks! Plus I have to change my router fairly regularly due to the state of the market for internet connections in the UK: usually you get the best deal by changing your supplier every 12 months, and with that you get a new router and the old one becomes e-waste. I prefer not to change the network settings in all of my devices when that happens but change the router settings when I first get it. So I want my computer to connect to any other network with that ESSID if the preferred BSSID isn't available.

Hope this helps somebody! To be honest, the *better* solution might be for NetworkManager to have some better logic for dealing with this common situation of dual-band home networks. Eg, if a 5GHz network is available, don't try connecting to 2.4GHz. But I'm not a developer and I'm not going to be the one to submit a patch, so I'll keep my mouth shut...

---

