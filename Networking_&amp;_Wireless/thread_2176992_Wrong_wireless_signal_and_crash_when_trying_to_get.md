---
title: "Wrong wireless signal and crash when trying to get wifi info"
date: 2013-09-26
forum: Networking &amp; Wireless
---

### Post by sadeqzadeh on 2013-09-26
I use a Dell Studio 1535 laptop  with an internal broadcom wireless adapter (NetLink BCM5784M Gigabit  Ethernet PCIe (rev 10)). Here is part of my lspci output:
```
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
```
Although I use Linux Mint 15, but since it is based on Ubuntu, I think you can help me a lot. I have two issues: 

1. The wireless signal  strength shown by wireless indicator in the tray (network manager) is  wrong and is oscillating all the time (from 99% to 70%, despite I'm  right next to my router). ```
iwlist wlan0 scan
``` indicates that my  signal strength is 99%-100% and also Conky displays the same strength (I've granted  Conky cap_net_admin and cap_net_raw root privilege levels). 

2. Whenever I run a program or a command (under root user privileges) that tries to access my wireless device directly to read info,my sytem crashes (a black screen like a full screen terminal shows up with some errors  indicating network manager has been stopped (and some error codes) and then X/window manager gets  messes up like when you have a problem with you graphic  card driver). I'm not sure if it's related to what I did or not, but I  installed wavemon, and it used to work properly when I was running it  under regular premissions, but again when I set cap_net_admin and  cap_net_raw privileges to its binary, or I ran it under root privileges, system  used to crash.  So, I removed it, but didn't get solved.
Here is the output of ```
iwlist wlan0 scan
```
```
wlan0     Scan completed :
          Cell 01 - Address: 98:FC:11:99:38:81
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"Javad"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 107196ms ago
                    IE: Unknown: 00054A61766164
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0E1017FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020079127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD1E00904C330E1017FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406050700000000000000000000000000000000000000
                     IE: Unknown:  DD9C0050F204104A0001101044000102103B00010310470010BC329E001DD811B2860198FC1199388110210011436973636F2053797374656D732C496E631023001B5741473132304E204144534C322B204D6F64656D20526F75746572102400075741473132304E1042000C53555730304B4332383932321054000800060050F20400011011000B5741473132304E20575053100800020084103C000101
```

---

### Post by varunendra on 2013-09-27
BCM5784M is not your wireless card, BCM4312 is. And it is supported by two different drivers, so if one is giving you problems, it is possible to have the other one work nicely.

To see which one is in use currently, please post back the output of -
```
lspci -nnk | grep -iA2 net
```

---

