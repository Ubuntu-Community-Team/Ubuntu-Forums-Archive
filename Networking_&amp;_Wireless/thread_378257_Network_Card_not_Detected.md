---
title: "Network Card not Detected"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by Justintoxicated on 2007-03-07
Hello I tried ubuntu over a year and 1/2 ago but I was not able to find any drivers for my network card so I switched to SUSE which worked fine.  Suse sucked though, my PC was way too slow running on it and woudl lockup every other day...Well not lockup but lag unbearably, so much that it was impossible to even shut the PC down and restart...

So I just built another old PC from my scrap pile and I'm having some Ubuntu install problems once again...

First I was not able to install on my new Raid-1 setup so i downloaded the alternative install CD.

Now the alternative install CD is saying that it is not able to detect my network card again.

I have 2 ISA network cards,  one is a 3Com Etherlink III and the other is an old netgear card.

What can I do to get one of these cards working!  I guss I could try SuSe again.....

---

### Post by Metaljaz on 2007-03-07
If the cards were not recognized by Ubuntu during install,
First you have to identify the cards and their chipsets that the cards are using.
From the terminal window type: 
lspci

The result of the network entry should be something like this:

02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Broadcom is the name of the card and BCM4306 is the chipset. So in this case you would have to find the drivers for the BCM4306. Then you would have to decide which method of install to do. Ndiswrapper using the windows drivers or use linux drivers if available.

---

### Post by Mr. C. on 2007-03-07
> **Justintoxicated said:**
> ...it is not able to detect my network card again.

I have 2 ISA network cards,  one is a 3Com Etherlink III and the other is an old netgear card.

What can I do to get one of these cards working!

Oh my, these are very old !

The Etherlink III, if I recall correctly, is supported by the 3c509 driver (if my memory is amiss, it would be the 3c59x driver).  Unfortunately, when Marketing folks create endless variations of same name, so its impossible for a consumer to easily determine from the product name, just what chipset is in the card.

ISA cards are not auto-detected.  You have to force that driver, and configure the interrupt and IO settings.  There are plenty of posts on the net about this i'm sure.

Not knowing the model of your netgear card, I can't say which driver it is.

> **Justintoxicated said:**
> .
I guss I could try SuSe again.....

Random responses to misunderstood problems is typically a path of failure.  Understand the problem before embarking on a fools errand.

MrC

---

### Post by Justintoxicated on 2007-03-08
Great thanks for the hope, now I just need to get it to complete the install process so I can even look into this.  I gave up on trying to get it to install through my Raid-1 array.  I looked though a number of tutorials but they always seem to start int he middle.  

After giving up on raid-1 I made it through once but the computer insists on a constantly rebooting.  So it is obviously not installed correctly.

These cards?  Old?  No Way I got them new with my first cable modem, I have many older parts than these!

---

### Post by zvacet on 2007-03-09
[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

---

### Post by Eniac on 2007-03-09
> **Metaljaz said:**
> If the cards were not recognized by Ubuntu during install,
First you have to identify the cards and their chipsets that the cards are using.
From the terminal window type: 
lspci

The result of the network entry should be something like this:

02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Broadcom is the name of the card and BCM4306 is the chipset. So in this case you would have to find the drivers for the BCM4306. Then you would have to decide which method of install to do. Ndiswrapper using the windows drivers or use linux drivers if available.


hum, now that is interesting, i have a similar issue, I recently installed ubuntu and its fine except that the lan card is not detected.

I already did lspci and it doesn't seem like ubuntu is detecting it at all because there is no mention of a network controller anywhere (but lots of unknown devices)

This is a brand new computer i just bought, it has video, lan and audio onboard and i suspect ubuntu is having problems with them.

you mentionned using the ndiswrapper ? i do have all drivers for windows, is it possible for me to use them at all in ubuntu ?

---

### Post by chili555 on 2007-03-09
Eniac-
This is from Ndiswrapper's site: > With ndiswrapper, most miniPCI (builtin), PCI, PCMCIA (Cardbus only) or USB wireless network card works in Linux with x86 or x86-64. Although ndiswrapper is intended for wireless network cards, other devices are known to work: e.g., USB to serial port device, ethernet card, home phone network device etc. See Wiki entry List for devices known to work.


Or to put it in other words, getting a LAN card to work is iffy.

The zombie geeks that haunt this forum have gotten some pretty weird stuff going. Tell us more about your card. Check the web for details about your computer, see if any secrets are listed in the manuals, etc. You might also try a command sudo lshw and see what network devices are listed.

You will probably have better luck if you start your own new thread, "Help getting Acme ethernet recognized" or similar.

Post back and let's see if we can get you going.

---

### Post by Eniac on 2007-03-09
> **chili555 said:**
> Eniac-
This is from Ndiswrapper's site: 

Or to put it in other words, getting a LAN card to work is iffy.

The zombie geeks that haunt this forum have gotten some pretty weird stuff going. Tell us more about your card. Check the web for details about your computer, see if any secrets are listed in the manuals, etc. You might also try a command sudo lshw and see what network devices are listed.

You will probably have better luck if you start your own new thread, "Help getting Acme ethernet recognized" or similar.

Post back and let's see if we can get you going.

I already got my own thread going but wasn't getting any response so i started searching for answer in other people's thread for similar issues.

I managed to get more precise info on the manufacturer's website, the manual it seems is made for windows only and gives very little info as to exact names of onboard devices.

I'll post that info in my own thread, i dont mean to hijack the OP's thread :)

[http://www.ubuntuforums.org/showthread.php?t=379756](http://www.ubuntuforums.org/showthread.php?t=379756)

---

