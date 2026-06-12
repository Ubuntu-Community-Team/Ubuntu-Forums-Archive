---
title: "bcm43xx restricted drivers install fine, but can't detect any networks"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by Chutney on 2008-02-19
Hi folks,

Followed the instructions here to install drivers/firmware for my laptop's wireless through "Restricted Drivers Manager":

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

Got to "In Use", everything seems fine, "iwconfig" and "lshw" seem to show the interface properly, and network manager behaves as if everything is going smoothly. However, neither Network Manager or "sudo iwlist scan" can detect any networks.

So far I've tried:

-confirming there are indeed active networks in range (yes).
-disabling all security from my home network to see if that helped (no).
-installing ndiswrapper (failed with "can't initialize module" or similar in the error logs)
-uninstalling ndiswrapper and trying above "Restricted Drivers Manager" procedure again (same result)

"lspci" says my wireless controller is: 

30:00.0 Network controller: Broadcom Corporation BCM 4312 802.11a/b/g (rev 02)


I'm reasonably handy with general Ubuntu troubleshooting (we have 5 PCs running Gutsy in the house) but don't know much about wireless issues (other times I have used wireless it has just worked straight away) so any help here would be greatly appreciated.

Thanks,

Chutney

---

### Post by jhetrick62 on 2008-02-19
Just because the driver installs properly and appears fine, doesn't mean that it is working fine unfortunately.

Ndiswrapper should work if installed properly.  I have it runnning on my laptop for a bcm43xx chipset on gutsy and I have it running on a ralink chipset on a desktop.

I would re-examine my ndiswrapper install procedures.

Jeff

---

### Post by Presto123 on 2008-02-19
Hey, I'm just curious about this, but do you have any linux-restricted-modules listed as installed on your machine? If you could, tell me what they are and I will compare them to mine. (Mine worked without a problem).

Also, did you get all of the updates? 

I'm curious about this, because I am wanting to understand what is causing so much of the issues with this card. FYI: It never worked for me in 7.04, but I installed (fresh)  7.10 and it worked out of the box.

---

### Post by jhetrick62 on 2008-02-19
I'm not loaded onto Ubuntu on that machine right now but I know for sure that I do not have any running, I uninstalled them when they didn't work.  I used ndiswrapper and never had another problem.  Don't know why they are squirelly, but it's not just the bcm chipsets.  Ralinks are tough too.

Jeff

---

### Post by Chutney on 2008-02-19
Presto,

I have all of the updates.

The linux-restricted-modules I have marked as installed are:

"linux-restricted-modules-2.6.22-14-generic"
"linux-restricted-modules-common"
"linux-restricted-modules-generic"

This is from a fresh install.  I haven't changed anything from default except updates, install restricted ATI drivers, and attempt to get wireless going.

---

### Post by Presto123 on 2008-02-19
Yes, I got to thinking about this post and realized that if you have it "working" to this degree, then it shouldn't be an issue with these modules. 

Thank you for posting that anyway.

---

### Post by Chutney on 2008-02-21
OK, for anybody else with the same issues, I solved eventually solved this the ndiswrapper way.

First time I tried ndiswrapper I used Vista drivers (sigh), without success.  Go with 
[XP Drivers from here]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-45290-1&lc=en&cc=us&dlc=en&product=3253950&os=228&lang=en") instead.

These instructions tell you all the commands needed,

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I used ndisgtk to make it even easier.  

Anyway, thanks to all the people above who tried to help me out with this.

---

### Post by jhetrick62 on 2008-02-21
No doubt, Vista drivers for wireless have been less than stellar.  I did not even expect that you would have used those, sorry!  Always use XP drivers with Ndiswrapper when possible.

Glad it works for you,
Jeff

---

### Post by DreamClown on 2008-03-05
> **Chutney said:**
> OK, for anybody else with the same issues, I solved eventually solved this the ndiswrapper way.

First time I tried ndiswrapper I used Vista drivers (sigh), without success.  Go with 
[XP Drivers from here]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-45290-1&lc=en&cc=us&dlc=en&product=3253950&os=228&lang=en") instead.

These instructions tell you all the commands needed,

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I used ndisgtk to make it even easier.  

Anyway, thanks to all the people above who tried to help me out with this.


WOOOOOT!!!!!one!!eleven!!!!!!!!

I've been trying for weeks following tons of how-to threads (complete with several Gutsy re-installs) and this finally got my bcm4312 (on a HPdv9000) working! Thanks a ton for sharing which method worked for you! 

Happily posting from a random room in my house while scratching and drinking a cold one,
~DC~

---

