---
title: "wireless card support AirCrack HELP PLEASE!"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by gohu_12 on 2008-04-14
Hello!

This is my first post on this forum,and i have few question...
I recently installed Ubuntu 7.10,and im fascinated with visual appearance,software...
I have Dell Inspiron 1501 notebook with Dell Wireless Card 1390 (Broadcom chipset - i think).
I use wireless card drivers which came with Ubuntu,i didnt installed anything other.
Yesterday i read something about AirCrack software,and i have questions:
-is my wireless card compatible with AirCrack, and will I be able to run this
-if it is compatible,how to install AirCrack on Ubuntu
If it's not compatible,please direct me to some kind of software with same purpose

I visited AirCrack website,but i got lost in all those pages,so i need you help
Sorry on my English,im from Bosnia and Herzegovina

Thanks

---

### Post by HunterThomson on 2008-04-14
If you are interested in AirCrack. You will want to be able to put your wireless card into "MONITOR  MODE"  and do "Packet Injection" I don't think your broadcom wireless chipset can do this but I will look for you. In any case you will need to install new driver to do it they are called IPRAW drivers. If you want to install AirCrack on your computer just type

sudo apt-get install aircrack-ng 

in the terminal and then aircrack-ng to start it.  However I would suggest you just download BackTrack3 for USB and install that Pen Testing Linux distro on a 1G USB drive. Or you could get the CD version. This is better then messing with the drivers on your real OS. As for a good wireless card to buy I Have a Linksys WUSB54G I got it for $50 at Radio Shack. Check out this video and web site.

[http://infinityexists.com/2008/03/08/episode-16-wireless-hacking-cracking-wpa/](http://infinityexists.com/2008/03/08/episode-16-wireless-hacking-cracking-wpa/)

You can type ifconfig -a   in the terminal to find out what wierless card you have... Or iwconfig

---

### Post by gohu_12 on 2008-04-14
wow!!
that was fast...
thank you for your answers,i will try this...
only im not shure will it work!i read somewere that broadcom cards are trouble...

---

### Post by HunterThomson on 2008-04-14
Ya I would stay way from the broadcom drivers....... I had the option of getting IPRAW drivers for my built in wireless chipset but I just sprung for the USB wireless device that I new would work grate. Also, I did install the RAW drivers for the WUSBGC onto Ubuntu and it crashed my computer and some how deleted the drivers for my intel chipset. That is why it is best to just download Backtrack and h4|< from there. The other grate thing about getting the USB Wireless card is that you can stay connected to a open AP with your built in wireless card and do packet sniffing with the USB one. It's worth the $50. It is also worth $20 for a 1G USB drive to install BackTrack3 USB too. BackTrack runs way faster from there and there is no CD spinning all the time and if you have to get moving fast you can because your hard drive is not spinning. You can still read/wright from the harddrive though. 

Watch that video....

---

