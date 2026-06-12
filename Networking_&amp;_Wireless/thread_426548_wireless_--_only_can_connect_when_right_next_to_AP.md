---
title: "wireless -- only can connect when right next to AP"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by cannednish on 2007-04-28
Hi,

I'm absolutely new to ubuntu (I've tried openSUSE before, but I decided to try out ubuntu). I've been trying to use my wireless card on my laptop -- IBM Thinkpad z60t. It's an Atheros wireless card, but after a lot of googling, I found out that this card now is supported in fiesty.

Anyway...in the nm-applet, I can see my wireless network and it's percentage (ranging from 20% to 70%...70% when i'm right next to the ap). When I connect it asks for my WEP key and tries to connect, but never does. In fact, I can't connect unless I'm sitting right next to the AP. I can't even be in the same room/across the room from it...I have to be sitting with my laptop touching the antenna on the AP. ](*,) 

any help?

---

### Post by Dorsai on 2007-04-28
Open the terminal and type:

sudo iwlist scanning

This should show you the details on any available connections, including the power level. It will look something like 83/100 or if low it might be 13/100 or something similar. Anyway post the output.

---

### Post by cannednish on 2007-04-28
Okay, I went to where I usually use my computer (it won't connect there). Here is the output.

Cell 02 - Address: 00:0F:A3:17:54:2A
                    ESSID:"lan"
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Quality=54/94  Signal level=-41 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

---

