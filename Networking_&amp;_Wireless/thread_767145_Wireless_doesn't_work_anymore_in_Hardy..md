---
title: "Wireless doesn't work anymore in Hardy."
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by Aeph on 2008-04-25
I installed ndiswrapper on Hardy, and configured the drivers for my wireless card. After I entered the information to connect to my network but when I tried to access the internet, I wasn't connected. Everything worked in Gutsy, and after hours of searching through the forums and Google, I have found nothing that helped.

Yes, my modem is on.
Yes, my wireless card is working.

---

### Post by Aeph on 2008-04-26
Finally found something that worked, so now I'm good.

---

### Post by calibre97 on 2008-04-26
And? What'd you do? I'm in the same boat. I had wireless working under 7.04, upgraded to 7.10 and it still worked and then I installed Kubuntu 8.04 RC and got it working with a PC Card but now I've got Ubuntu (wanted to check out Gnome) 8.04 real version but no wireless.  Can you post what it was you found/did to get things working?

---

### Post by calibre97 on 2008-04-26
Nevermind. :popcorn:

Trying Linux out? KEEP A 50' Ethernet cable handy!!!!

So I strung the cable from the DSL/wireless modem/router setup and got connected. Of course that works. I used Synaptic to install NDISWRAPPER utils and common and then used Add/Remove to install Windows Wireless Drivers GUI. With that installed and running, I selected the .inf file I had already copied to the shared Windows/Linux partition, and then BAM, Bob's yer uncle. Wireless with the D-LINK DWA 652 works. I ain't even gonna try the built-in Broadcom madness. This works.

---

### Post by Ceox on 2008-04-26
How do you install the wrapper when you don't have internet in Ubuntu?

---

### Post by brew1brew on 2008-04-26
check [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"), most of the way down there is a fix for Hardy. It worked on BCM94311MCG wlan mini-PCI (rev 02).

Les

---

