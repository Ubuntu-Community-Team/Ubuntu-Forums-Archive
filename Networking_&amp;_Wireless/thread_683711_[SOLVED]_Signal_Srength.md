---
title: "[SOLVED] Signal Srength"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by tad1073 on 2008-01-31
My essid has a signal strength between 25% and 35% but there are essid's, about 5 or 6 of them, that show up on wireless networks that are maxed out so that should mean that there is either a wireless router next to my computer or some one that is within 5 to 10 feet running his wireless card as a duplicator, right. Well, the only problem is, is that there is no one around me. I at home, upstairs in my room. Could someone explain this enigma to me.

---

### Post by tad1073 on 2008-01-31
bump

---

### Post by lungdart on 2008-01-31
Well theres two real options of whats happening:

1) All the other ESSID's are much stronger then yours/better paths to you

2) The software/driver/hardware combination for your wireless card is not giving you a true readout of signal strengths.

There have been known problems with signal strengths with ndsiwrapper and broadcom devices.

In order to understand what is causing this problem we need more information.

What hardware are you using for wireless (NIC and Router)?
How did you set up wireless in Ubuntu?
Which kernel and version of Ubuntu are you running? (uname -a)
How are you checking signal strengths? (iwconfig?)
Is anything showing up in your system logs regarding any errors with your wireless setup?
Also, do you have any other wireless devices that are picking up those ESSIDs as well, and what are there setups and signal strengths?

---

### Post by tad1073 on 2008-01-31
D-Link DI-624 router

```

thomas@computer:~$ uname -a
Linux computer 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
 
thomas@computer:~$ lspci
00:00.0 Host bridge: Broadcom CNB20LE Host Bridge (rev 05)
00:00.1 Host bridge: Broadcom CNB20LE Host Bridge (rev 05)
00:01.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03)
00:02.0 Ethernet controller: Atheros Communications, Inc. 
             AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
00:0f.0 ISA bridge: Broadcom OSB4 South Bridge (rev 4f)
00:0f.1 IDE interface: Broadcom OSB4 IDE Controller
01:04.0 SCSI storage controller: LSI Logic / Symbios Logic 53c895a (rev 01)
01:05.0 Ethernet controller: Intel Corporation 82557/8/9 Ethernet Pro 100 (rev 08)
01:06.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
01:07.0 System peripheral: 
             Compaq Computer Corporation Advanced System Management Controller


thomas@computer:~$ iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: not important
                    ESSID:"thompson"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-75 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:ath_ie=dd0900037f0101001f0000
          Cell 02 - Address: 00:16:B6:CE:E3:73
                    ESSID:"thetownsendwilliamsfamilyrock"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=5/70  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:18:39:F3:60:B8
                    ESSID:"Wade"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=5/70  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:1A:70:6B:A7:98
                    ESSID:"Beach"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=5/70  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 05 - Address: 00:1A:70:57:89:67
                    ESSID:"4eveler"
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Quality=223/70  Signal level=-128 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 06 - Address: 00:18:39:46:39:55
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=2/70  Signal level=-93 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 07 - Address: 00:18:39:B5:39:B1
                    ESSID:"ddrule"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=255/70  Signal level=-96 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 08 - Address: 00:90:4C:7E:00:10
                    ESSID:"NETGEAR"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=255/70  Signal level=-96 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 09 - Address: 00:0D:72:DF:2C:99
                    ESSID:"2WIRE036"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=249/70  Signal level=-102 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=100
          Cell 10 - Address: 00:12:0E:7B:76:E8
                    ESSID:"WEST7221"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=2/70  Signal level=-93 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 11 - Address: 00:18:3A:41:2A:E0
                    ESSID:""
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-61 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK

```

> 
How did you set up wireless in Ubuntu?


I don't understand the question.

> 
How are you checking signal strengths? (iwconfig?)


i either look at conky or hover over the icon to check my signal strength or click the icon and check the other AP's by lookking at the bars.

---

### Post by lungdart on 2008-02-05
1) I meant when you installed ubuntu did your wireless work right out of the box? Or did you use the restricted driver manager to install them, or any tutorials using ndiswrapper or fwcutter?

2) Your signal strength does seem low, but on the other hand so is everything else.
This tells me that it is probably a support issue. As I see your using an Atheros chip set, I would assume that is supported natively within the linux kernel. Unfortunately that leads me do a dead end, unless you want to go around looking for tips and tricks to increase Atheros signal strengths.

---

### Post by tad1073 on 2008-03-11
> **lungdart said:**
> 1) I meant when you installed ubuntu did your wireless work right out of the box? Or did you use the restricted driver manager to install them, or any tutorials using ndiswrapper or fwcutter?

2) Your signal strength does seem low, but on the other hand so is everything else.
This tells me that it is probably a support issue. As I see your using an Atheros chip set, I would assume that is supported natively within the linux kernel. Unfortunately that leads me do a dead end, unless you want to go around looking for tips and tricks to increase Atheros signal strengths.

My card worked out of the box.

i am on the second floor, about 15ft. up and 25ft. over with walls and other electronics, radios, tv's, microwaves etc.

---

