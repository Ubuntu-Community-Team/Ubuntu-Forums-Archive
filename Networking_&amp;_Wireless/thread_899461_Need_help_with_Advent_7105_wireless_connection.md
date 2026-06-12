---
title: "Need help with Advent 7105 wireless connection"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by cymrupl1 on 2008-08-24
I'm new to Linux and have just installed Ubuntu 8.04 on my Advent 7105 laptop but cannot get the wireless to work.  I have tried following various threads on installing a driver for this card but I am at a loss as to how I should download and install a driver for it.  The computer has a hotkey for the wlan but this does not work with Ubuntu.  I really need a clear and simple explanation (for a complete novice) on how this is done.

The card is a Marvel Technolgy Group Limited 88w8335[Libertas] 802.11b/g wireless (rev 43).

Grateful for any help!

---

### Post by reddragon2282 on 2008-08-25
Hi, I have the exact same problem and have had for some time now. Have you had any break throughs yet mate.

---

### Post by cymrupl1 on 2008-08-26
Still not solved if anyone can help!!

---

### Post by reddragon2282 on 2008-08-26
Still no luck then mate this problem is doing my head in is there anyone who can help.

---

### Post by reddragon2282 on 2008-08-27
I think we may have to use the NDISWRAPPER  can anyone shed any light on the subject.

---

### Post by GrandpaLeaman on 2008-08-27
I didn't see anything current on this issue, but there was a thread from last year:

[http://ubuntuforums.org/showthread.php?t=208088](http://ubuntuforums.org/showthread.php?t=208088)

Hope this points you in the right direction.

---

### Post by tim525l on 2008-09-10
I'm not sure if your laptop is the same, but I've recently managed to get Xubuntu working with my Advent 7040 laptop.  The problem I had was that when I pressed the WiFi button, it didn't activate the Wifi.

I have installed Xubuntu 8.04 on a partition with XP on the other partition.  

Then I went into the Bios and set the WiFi activation to maintain is't condition that it was last switched off in.

Then re-start in Ubuntu, and your WiFi will be active.

I'm sure other people have cracked this before, but I couldn't find another post and was quite proud of myself as a complete newcommer to the world of non-Microsoft computing!

Hope it helps...

---

### Post by tim525l on 2008-09-10
I forgot to mention that After changing the bios, I started up in XP, turned on the WiFi then restarted in Xubuntu.

it's been a long night  ;)

---

### Post by lilmale1 on 2008-09-10
if you still need help let me know

---

### Post by reddragon2282 on 2008-09-12
Yeah we could get it to work that way but I have removed XP totally and now it doesn't work at all. I press the button and it doesn't activate my wireless. So i need to get some sort of linux friendly driver for the wireless card.

---

### Post by izzle_master on 2008-09-15
I'm having the same issue.  I attempted the BIOS approach, but to say BIOS is limited on the Advent 7105 would be an understatement.  Any help would be greatly appreciated.

---

### Post by reddragon2282 on 2008-10-15
I have finally got the wireless to activate by the switch and it does pick up the wireless networks but when I try and connect it asks for my passphrase or network key. I enter the WEP KEY and it searches. But nothing happens can anyone shine any light on this subject, Do I need to alter any settings.

---

### Post by mtn on 2010-11-28
I have an Advent 7105 with Marvel Technology Group Limited 88w8335[Libertas] 802.11b/g wireless (rev 43) - pciid: 11ab:1faa  - I have been banging my head off a brick wall all day trying to get the wireless to work.

I have followed a bunch of threads here, and else where, including this one that says it is solved: [http://ubuntuforums.org/archive/index.php/t-521045.html](http://ubuntuforums.org/archive/index.php/t-521045.html)

As well as following the Ndisawrapper Wiki installation guide: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Disable%20Free%20Drivers](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Disable%20Free%20Drivers)

I have tried 3 different drivers from here: [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Special%3ASearch&search=11ab%3A1faa&fulltext=Search](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Special%3ASearch&search=11ab%3A1faa&fulltext=Search)

I can't get it to work. I number of times the wireless LED on the laptop has come on but then things have frozen up and I have had to remove the drivers to get things working again.

In the end I got a TP-Link 54Mbps TL-WN321G wireless USB adapter (which literally "just worked" when I plugged it in), connected it with a short USB extension cable and duck tapped it to the outside of the laptop's lid. Not that pretty but it works very well indeed and with 4 USB ports it is not such a big pain.

However, if anyone has got the Marvel Technology Group Limited 88w8335[Libertas] 802.11b/g wireless (rev 43) to workI would be very interested to know how?

Cheers, M

---

### Post by andrewkar on 2012-10-27
Hey,

Yeah, I know it's old. Anyway...

I managed to get it to work, and it works perfectly! (you can do what you like with it).

OK, so first thing first. 

Most people don't differentiate between version rev3 and rev43.

Rev3 is for USB network cards and rev43 is for build in laptops chips (at least this is what I think). 

I managed to get it to work on laptop Advent 7105 with Marvell Libertas rev 43 under Xubuntu 11.10.

Now, to make it work you need Ndiswrapper and proper driver. So for everyone who is strugling with build in marvell libertas the right driver is called:

**Marvell_Libertas_8335_v3.2.3.2**

This is what you need to make it work.

Inf.file is called:
[B]
netmw125.inf[/B]

but you will need other files also  (sys.) to get it to work  so look for:

**Marvell_Libertas_8335_v3.2.3.2**

If you have problems finding it just Google:

marvell libertas 8335 3232 (rev43)

That's it.

Cheers

Andrew

P.S I have managed to work it under Win7 as well but with another, different inf. file (officially it has no support from MS...).

**** MS, we can make it anyway ;):guitar:

---

### Post by wildmanne39 on 2012-10-27
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

