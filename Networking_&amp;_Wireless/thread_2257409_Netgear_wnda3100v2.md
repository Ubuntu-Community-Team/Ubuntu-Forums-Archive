---
title: "Netgear wnda3100v2"
date: 2014-12-19
forum: Networking &amp; Wireless
---

### Post by trevis2 on 2014-12-19
I am fairly tech-savvy normally, but I am stumped here.  I have a netgear wnda3100v2 usb wireless adapter, and have installed the windows 7 driver for it using ndiswrapper.  I go to ifconfig and no wlan0 shows up.  I am unsure of how to proceed next, as all of the tutorials I have read about this pretty much say to ask here if their procedure doesn't work.  I am coming from a windows 7 environment.  I know you will ask, so here's some info:

PC:~$ lspci -nn | grep 0280

PC:~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 1a2c:0023 China Resource Semico Co., Ltd 
Bus 003 Device 003: ID 19ff:0238 Dynex 
Bus 003 Device 002: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

PC:~$ rfkill list all

I have no idea what I'm doing wrong.  Let me know if there is other info you need.

---

### Post by jeremy31 on 2014-12-19
I thought XP drivers were needed when using ndiswrapper?

---

### Post by trevis2 on 2014-12-19
I do not know.  Are they?  How would I remove the windows 7 driver?

---

### Post by jeremy31 on 2014-12-19
To unload a driver you could find the driver name in terminal history with```
history | grep ndiswrapper
``` and find the one that says ndiswrapper -i with the .inf file and copy that but replace -i with -r to remove
Another thread says this [http://media.cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz)[COLOR=#000000][FONT=verdana]  should work
[/FONT][/COLOR]

---

### Post by trevis2 on 2014-12-19
Well, that got the wireless adapter recognized, thank you so much for that.  Unfortunately, it keeps asking for the network password over and over again, even though I am entering the right one.  So, now I need to figure that one out.

---

### Post by jeremy31 on 2014-12-19
> **trevis2 said:**
> Well, that got the wireless adapter recognized, thank you so much for that.  Unfortunately, it keeps asking for the network password over and over again, even though I am entering the right one.  So, now I need to figure that one out.

That might be a sign that the router is not using WPA2-AES only, using WEP or TKIP usually results in problems with some routers.  You could run the wireless script from the sticky post "before posting in networking and wireless" and look at the wireless-info.txt file to see for yourself what the available routers are using, or you could look at the results of ```
iwlist scan
```
You don't want to see this```
IE: IEEE 802.11i/WPA2 Version 1                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```

You want to see CCMP instead of TKIP

---

### Post by trevis2 on 2014-12-19
Result of iwlist scan (sorry, don't know how to do the "Code:" window)

Code:
PC:~$ iwlist scan
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: B0:05:94:19:C5:C5
                    ESSID:"PS4-B35612527C8C"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality:89/100  Signal level:-39 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00105053342D423335363132353237433843
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C1103FFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1607080000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: E4:F4:C6:11:8C:4B
                    ESSID:"Mine"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality:82/100  Signal level:-43 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00044D696E65
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B0509001A0000
                    IE: Unknown: 2D1AAD1917FFFFFF0001000000000000000000000000000000000000
                    IE: Unknown: 3D1607080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080500080000000040
                    IE: Unknown: DD7A0050F204104A0001101044000102103B00010310470010DF31C9E3E0E6BAD4B38376E662CBF7DE1021000D4E4554474541522C20496E632E1023000552373030301024000552373030301042000233321054000800060050F2040001101100055237303030100800022008103C0001031049000600372A000120
                    IE: Unknown: DD090010180209001C0000
                    IE: Unknown: DD180050F2020101840003A4000027A400004243BC0062326600
                    IE: Unknown: 46057200010000
                    IE: Unknown: DD1E00904C0408BF0CB259820FEAFF0000EAFF0000C0050007000000C3020002
          Cell 03 - Address: 28:C6:8E:C5:77:EA
                    ESSID:"MOMSCOMPUTER-PC_Network"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Quality:29/100  Signal level:-77 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00174D4F4D53434F4D50555445522D50435F4E6574776F726B
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030102
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34020D0A00000000000000000000000000000000000000
                    IE: Unknown: 3D16020D0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD8E0050F204104A0001101044000102103B000103104700100000000000001000000028C68EC577EA1021000D4E6574676561722C20496E632E10230009574E523130303076321024000456324831104200046E6F6E651054000800060050F20400011011001E574E523130303076322D564328576972656C6573732041502D322E344729100800020086103C000103

Cell 2 is the one I am trying to connect to.  The router is definitely on WPA2, and the password is definitely correct.  I am unsure of where to go from here as most of the troubleshooting I have seen in the forums hasn't seemed to work for me.  I have some decent training in networking, just not linux (seems ironic, doesn't it).  Could it be a driver issue?  Is there any other USB sticks out there that might be a better match for linux?  Especially ones that are 802.11ac?  My router died about a week ago and I used the opportunity to get an upgrade.  BTW this ubuntu box is going to be used as a media server (found windows to be too unstable for that use for my tastes).  Thanks a lot for all of your help.  Once I get internet, things should be better.

---

### Post by jeremy31 on 2014-12-19
Some here like to have the routers fixed on channel 1, 6, or 11
Is the AC enabled on the router, if it is disable it to do some testing to see if you can connect then.  I have seen this [https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux](https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux) recommended before but I haven't bought from them.  Most of my laptops have intel wifi cards in them and one has an Atheros.  If you can get an Intel wifi card for that computer it should be supported under Linux

Code tags, in front of what you want tags around it is code inside of [] and at the end you use /code inside of the brackets, in the advanced reply window, there is a '#' symbol you can click to have the tags placed for you and then you just paste

---

### Post by trevis2 on 2014-12-19
Yeah, 7 is the best, most open channel in my area.  In my experience, the difference is negligible.  I have disabled AC until I have something running AC.  Do you know of anything else that might prevent me from logging in now (or anything I can try)?  I have been trying to get the network going all day, and I am ready to just call it quits.

---

### Post by jeremy31 on 2014-12-19
> **trevis2 said:**
> Yeah, 7 is the best, most open channel in my area.  In my experience, the difference is negligible.  I have disabled AC until I have something running AC.  Do you know of anything else that might prevent me from logging in now (or anything I can try)?  I have been trying to get the network going all day, and I am ready to just call it quits.

In my opinion, ndiswrapper is a bandaid on a broken leg and it has been called worse, any option that doesn't involve it is a better option.  I did play around with a netgear WNA3100 USB wifi that I had and wasn't impressed with the results and there wasn't any solution in sight and the only option was ndiswrapper

Did you use the correct inf file based on your installed Ubuntu version, if you use 64 bit Ubuntu, you need to use the 64 bit inf file

---

