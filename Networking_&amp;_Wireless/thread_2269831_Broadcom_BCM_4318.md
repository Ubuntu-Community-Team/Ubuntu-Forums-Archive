---
title: "Broadcom BCM 4318"
date: 2015-03-18
forum: Networking &amp; Wireless
---

### Post by hunter8 on 2015-03-18
New to all this. Never posted in a forum before. Have downloaded 3 different versions of Ubuntu to "revive an old laptop" as advertised. You know who, (XP) quit me, I didn't quit them.  Interested in trying something new to get away from you know who.  Love the idea of open source, but.....  Each version loaded and performed with one huge exception, none will find my wifi capability. I am assuming as I wiped out XP, drivers went with it.  Since read probably 10k words on the subject of Umbuntu-wifi to no avail. Wish I would have known that before embarking on this project. So now I have a glorified DVD/CD player.  Tried to get drivers by downloading Umubtu updates-locked up and wouldn't even shut down, tried to get drivers-nothing, tried 6 different programming suggestions-nope.  There is so much forum time written on this subject, I'm astonished it hasn't been resolved by now.  OK, Acer Aspire 3690, 32-bit, 5++mg of RAM, Broadcom BCM 4318 [Air Force One 54g] wireless controller (rev02).

Help a brother out. I want to be a Linux brother but.....

---

### Post by slickymaster on 2015-03-18
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by Bucky Ball on 2015-03-18
Well, I'll do the best I can. If you know for sure it is BCM4318, best thing to do is get online with an ethernet cable, update and then check Additional Drivers for the B43 driver for your card.

Alternatively, if you can get online with a cable, follow the instructions for installing B43 for 12.04/14.04 from [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29_-_14.04_.28Trusty_Tahr.29"). Much easier than if you can't get online with a cable, in which case you should try [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access"). 

Good luck and welcome to Ubuntu/the forums. ;)

PS: I'm presuming you are using 14.04 LTS (long-term support until 2019), 12.04 LTS (2017) or 14.10 (this July I think)? Please clarify. Also, to verify it is the BCM4318, open a terminal and:

```
sudo lshw -C network
```

That will show you the network controller (wireless chip) and the driver it is using, if any. Because you tweaked, poked and prodded, it may be necessary to blacklist or remove any other driver you've installed, but see how you go following the above instructions.

---

### Post by Hadaka on 2015-03-18
Hi, from a working wired connection, please do..
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```

---

### Post by Bucky Ball on 2015-03-18
+1. Go with Hadaka's advice. More knowledgeable in these matters than I. ;)

---

### Post by mörgæs on 2015-03-19
An Aspire 3690 is weak hardware. I suggest Lubuntu and not Ubuntu.

---

