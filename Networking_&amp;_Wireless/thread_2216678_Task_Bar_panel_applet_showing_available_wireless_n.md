---
title: "Task Bar panel applet showing available wireless networks"
date: 2014-04-13
forum: Networking &amp; Wireless
---

### Post by mattw1 on 2014-04-13
I am new to Lubuntu and love it so far.  Can anyone please tell me how I enable the "available wireless networks" icon -or  something that tells what wireless connections are available - on the  bottom task bar?  I've looked through all off the "already posted" answers and nothing seems to address this issue, or at least give me an answer that works.  I've also looked through all of the available panel applets  but can't seem to find one for that purpose.  I am assuming that there has to be one.  Btw, I am connected at this point.  When I was first installing Lubuntu a screen came up with all of the available networks and I logged in at that time.  It has logged me in automatically since but I have no idea where to go if I were to try to log on to different network.

Thank you.

Matt W
Lubuntu 14.04
IBM Thinkpad T42
Pentium M
1.70 Ghz
768mb RAM
60gb HD

---

### Post by praseodym on 2014-04-14
Try to start the applet from terminal:
```

gksudo nm-connection-editor
```

---

### Post by mattw1 on 2014-04-14
Yes, thank you, I appreciate your help but I can get to that particular applet fine through the menu.  But it only shows the network that I am connected to.  I am looking for a list of all available networks.   On my other laptop running in the same room I can get signals from from 16 other routers (I live in a condo).  I run two routers and two repeaters myself for a variety of reasons and all of those routers are within 40 ft of each other.  How can I "see" these other networks?

Thanks again.

---

### Post by praseodym on 2014-04-14
First, try

```
nm-applet
```

If its not working check the manual scan:
```

sudo iwlist scan
```

---

### Post by mattw1 on 2014-04-14
I typed in    nm-applet    and this is what came up:

tpad@tpad-ThinkPad-T42:~$ nm-applet
nm-applet-Message: using fallback from indicator to GtkStatusIcon

Then I typed in    sudo iwlist scan    and this is what came up:

tpad@tpad-ThinkPad-T42:~$ sudo iwlist scan
[sudo] password for tpad: 
irda0     Interface doesn't support scanning.

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 02:24:B2:00:A0:B5
                    ESSID:"5MA9T"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=95/100  Signal level=-32 dBm  
                    Extra: Last beacon: 12ms ago
          Cell 02 - Address: 00:7F:28:58:3A:DB
                    ESSID:"CG47B"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=39/100  Signal level=-77 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 48ms ago


I don't know what any of that means.  Can you help me to understand the basics?  Thank you.

---

### Post by praseodym on 2014-04-14
It only shows 2 networks. One is yours?

---

### Post by mattw1 on 2014-04-14
Yes, 5MA9T

---

### Post by mattw1 on 2014-04-14
Just downloaded a program called "Wifi-Radar".  Seems to do the trick.  Thanks so much for your help, Praseodym.   Matt

---

