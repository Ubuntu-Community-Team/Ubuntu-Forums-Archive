---
title: "linksys details please"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by cmitcham on 2007-09-27
i have installed 7.04 on an old machine. it would be great if i could get my wmp54g working with WAP. i don't know if it's a version 4 or 4.1, but i 'm guessing it's a 4.1 since what i found talked like 4 would work right out of the box. what i did find (for v4.1) was:

*Works only in Feisty if you put to "blacklist" the "rt61pci" module BEFORE install the card. If not, your computer will freeze often. There is an other module: "rt61" it works fine, with WEP too. *

the card was in the machine when i did the install before i started all this searching for answers, so should i remove the card and reinstall before i spend any time getting this install fine-tuned? the install is destined to become a ubuntustudio system.

thanks!

---

### Post by noob12 on 2007-09-28
If you post the output of **lspci -nn**,  people can see the id of the device you actually have, and that might lead to a suggestion.

---

### Post by cmitcham on 2007-09-28
thanks for the help! lspci -nn says :

00:0f.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)

now i would like to change my question. i see a trip to compusa in my near future. this machine has no dvd burner and only 256mb ram. so i'm willing to buy a new wireless card while i'm there. if anyone can, i would love to hear a make and model of card i could buy to just install and work.

i have googled, and have read alot about using ndiswrapper, removing ubuntu's nice little network manager gui, etc. alot of the time, it's hard to tell if what i'm reading is three years old and outdated or what. the list that claimed to be THE list of linux supported cards colored my wmp54g just as green as it could be.

i don't mean to be sounding like the whiners, the fact is that wireless just isn't important enough on this box to go to any more trouble than install and it works. if this machine must talk with the world, i just carry it downstairs to a cat5 cable, or run a long cat5 cable to it.

(my last house was about 975 sq. ft. and had over half a mile of cat5 cable. we moved and i vowed to be wireless.)

thanks for reading, and let me know of any wireless card you know works with 7.04, no ndiswrapper, talks wpa-personal, and likes ubuntu's graphical manager.

---

### Post by horrorpunk138 on 2007-09-28
I just had to get a new wireless card/stick a couple days ago. I'm running 7.04 on a V6000 and bought the Linksys WUSB54GC for 30 bones.

Using this guide...

```
http://ubuntuforums.org/showthread.php?t=516649&highlight=WUSB54GC
```

I just popped the USB stick back in and runs like a champ.

Hope that helps. :)

---

### Post by horrorpunk138 on 2007-09-28
*NOTE FOR ABOVE POST*

It will try to "plug and play"...but doesn't work. You'll have to install ndiswrapper, but using that guide, the original author wrote a fantastic script that does it all for you.

---

### Post by noob12 on 2007-09-29
This is version 4 of the card with the Ralink RT2500 device.

For Feisty, I'd suggest downloading and building a recent version of ndiswrapper 1.47 or 1.48 and using that with the XP driver for the card.

I think Gutsy may be ok with a current build of the rt2500 driver source downloaded from serialmonkey.

---

