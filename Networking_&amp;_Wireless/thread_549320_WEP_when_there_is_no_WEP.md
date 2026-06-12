---
title: "WEP when there is no WEP"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by ladynikon on 2007-09-12
I am at school.  Today when I signed on.. the schools WAP was showing up as WEP encrypted but its not.  It didn't show up yesterday as ecrypted either.  In windows ( my laptop is dual booted) it also does not show up as encrypted. 

Anyone ever have this?

Ladynikon:guitar:

---

### Post by wieman01 on 2007-09-12
If you posted the results of:
> sudo iwlist scan
...we'd know. :-)

---

### Post by ladynikon on 2007-09-13
sorry this took so long.  I had to get an inet connection...:lolflag:

BTW " I can't do an IF .. if I had no idea.. what the command was :p

"sudo iwlist scan"

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:06:B1:2D:CC:E9
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:10
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=66/100  Signal level=-67 dBm  Noise level=-67 dBm
                    Extra: Last beacon: 188ms ago
          Cell 02 - Address: 00:11:5C:A9:20:20
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:8
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=46/100  Signal level=-81 dBm  Noise level=-81 dBm
                    Extra: Last beacon: 556ms ago
          Cell 03 - Address: 00:11:5C:A9:1E:90
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:5
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=38/100  Signal level=-86 dBm  Noise level=-86 dBm
                    Extra: Last beacon: 220ms ago



Just so you know.. I talked to helpdesk.. The answers I got was " maybe we are blocking linux" , " just use windows" , " maybe its trying to connect to the WAP before ..." so yeah no help from there.

The essid is indeed hidden.  You have to tell the computer its there.. and my computer knows its there.

---

### Post by wieman01 on 2007-09-14
What wireless device have you got? You scan indeed suggests that it is WEP, however, it might due to the fact that your wireless driver does not support WPA at the moment.

---

### Post by ladynikon on 2007-09-14
> **wieman01 said:**
> What wireless device have you got? You scan indeed suggests that it is WEP, however, it might due to the fact that your wireless driver does not support WPA at the moment.

it is the intel centrion wireless card.  It has worked fine dozens of time before hand.  :mad:

---

### Post by ladynikon on 2007-09-17
still no clue?

---

### Post by kevdog on 2007-09-18
There are 3 results posted in you iwlist scan results.  One is unencrypted, and two are encrypted via WEP.  Are these broadcasts all the school's, or possibly other networks nearby with WEP encryption?

---

### Post by skycrawler on 2007-09-18
I have heard of this technique whereby a hacker creates a wireless network with same essid to attract computers to connect to it and thus he can sit and snif packets. 
This is more near school and university vicinities with lots of wireless users.

---

### Post by ladynikon on 2007-11-06
> **kevdog said:**
> There are 3 results posted in you iwlist scan results.  One is unencrypted, and two are encrypted via WEP.  Are these broadcasts all the school's, or possibly other networks nearby with WEP encryption?

all at my school.  This is now happening on my fellow classmates laptop.  He is running gutsy gibson too.. My coworker at my computer lab got mine kinda working.. we had to turn roaming off and now I do not have it autoconnecting to the essid that is already listed.  So this has to be a problem with ubuntu. It still works perfect in windows.

---

### Post by kevdog on 2007-11-06
Glad you connect -- From what I have gathered in the forums, is possible that the wireless tools package and hidden essid networks may cause a problem.  Not sure why, but that is why its advisable for most linux users to turn their essids on.  Of course if you are not in control of the AP, that is hard to do!

---

### Post by ladynikon on 2007-11-06
> **kevdog said:**
> Glad you connect -- From what I have gathered in the forums, is possible that the wireless tools package and hidden essid networks may cause a problem.  Not sure why, but that is why its advisable for most linux users to turn their essids on.  Of course if you are not in control of the AP, that is hard to do!


yep,
The school thinks its a security feature to have the WAP not broadcast.  I was hoping having gutsy would fix this problem :(.

---

### Post by kevdog on 2007-11-06
Are you meaning 

WEP, WPA, or WAP??

---

### Post by ladynikon on 2007-11-17
WAP.  The ESSID does not broadcast.

---

### Post by kevdog on 2007-11-17
There are a few scanner utilities available for Linux -- Kismet comes to mind but I think there are others -- that are able to scan for hidden SSIDs.  I dont think that these utilities help you connect, however they at least discover hidden Essids.

---

### Post by wieman01 on 2007-11-17
Kismet and the likes (e.g. Airodump) let you detect the name of a network with disabled broadcast of the SSID as soon as a client connects to it. That is because clients transmit that piece of information in order to associate with a wireless network.

---

### Post by ladynikon on 2008-03-27
Anyone have any ideas?  I am still having this issue?  It seems the only way to connect is either by cat5 or reinstalling ubuntu!  Help :(

I tried doing this in the command line..
"iwconfig eth1 essid <essid> key off"

I figured it out! i had to do dhcpclient eth1 ! yes!

---

