---
title: "Realtek 8187 Trouble in Gutsy"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by logicalfrank on 2008-03-28
I am running Gutsy and have a USB wireless card w/ the Realtek 8187 chipset and I cannot get it working for the life of me. W/ the automatically installed drivers, The card was foundand I could see networks listed but could not connect to any wireless networks (even unencrypted). I installed ndiswrapper 1.52 (compiled the code myself--I guess there is an easier way but I just followed the readme file) and installed the win98 driver as suggested and blacklisted the other, non-working driver. Now it does not seem to detect a wireless card at all.

 If I run lsmod, this line is included:

ndiswrapper           193436  0

ndiswrapper -l yields:

net8187b : driver installed
        device (0BDA:8187) present (alternate driver: rtl8187)

lsusb gets me:

Bus 005 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000 

So that would seem like everything is in line, right? But my little network manager applet thingy doesn't have any wireless devices listed.

These forums have been very, very helpful in me getting this far but I'm at about the end of my Linux capabilities here and still haven't got it figured out. Any advice on how to proceed? Thanks in advance.

Also, I thought I might mention some strange behavior I noticed when using the native driver. When I tried to connect to my old 2wire 1000HW, it caused it to reset (!?) so it would seem that my wireless card is sending out something but whatever my modem is receiving is all kinds of wrong. I have tried a couple other modems and it simply does not connect. Everything works fine, card and modems, in XP.

---

### Post by jimmyridge on 2008-03-29
yeah i hate the module rtl8187  
it kept overriding r8187 (aircrack insjection patched version i use)   
took me forever to realize i was modprobing rtl8187 not r8187  (until i blacklisted rtl8187 ) muwahaha r8187.ko rocks on my box.

[http://www.aircrack-ng.org/doku.php?id=r8187](http://www.aircrack-ng.org/doku.php?id=r8187)

i dont really use it to connect just attack ;) its a goofy card 
a bit finiky like sometimes i have to constantly "ifconfig wlan0 up"  after iwconfig changes  and then dhcpc works i dunno lets figure it out eh?

ps grab the latest svn of aircrack.. ;)

```

svn co http://trac.aircrack-ng.org/svn/trunk/ aircrack-ng 

```


OMFG i just realized your using ndiscrapper AHH stay away from it, reminds me of the guys using it for atheros cards! jeez no Windows®&#8482;  drivers on my boxz pleaze thanx

---

### Post by logicalfrank on 2008-03-29
Thanks very much. That worked. I had actually tried a different patch I found w/o success but this one seems to work great. Very easy to install. Posting from my wireless connection now.

---

### Post by egooey on 2008-03-31
> **logicalfrank said:**
> Thanks very much. That worked. I had actually tried a different patch I found w/o success but this one seems to work great. Very easy to install. Posting from my wireless connection now.

can you explain more what did you do to make it work? i have the same problem with you

---

### Post by jimmyridge on 2008-04-03
you really should read/think before you post ;)

---

