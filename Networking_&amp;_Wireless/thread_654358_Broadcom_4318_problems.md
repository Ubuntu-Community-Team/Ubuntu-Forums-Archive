---
title: "Broadcom 4318 problems"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by BordrGuy108 on 2007-12-31
Hey all. I've been trying to get Ubuntu set up on my HP Pavillion Zd8000 for a few days now and so far I've been unsuccessful in getting the wireless to work (I have a Broadcom 4318 card). I've searched the forums and attempted to follow many guides and how-to's to the point that now I'm afraid I've screwed up my network manager settings. When I click on the little network icon next to the clock on my top bar I no longer see the same options available as I did by default right after my install of Gutsy. I have two main questions:

First, is there any way to revert my Gutsy install back to all the default settings as if it were freshly installed? I was messing with all these network settings and also looking into some overheating issues and I am thinking I should maybe start over, but was wondering if there is an easier way than reinstalling.

Secondly, I can detect the wireless network I'm trying to connect to, but after I enter in all the information, it attempts to connect, but when I go to firefox I can't connect to any pages... I've tried following these posts so far without success:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)
[http://ubuntuforums.org/showpost.php?p=1189681&postcount=105](http://ubuntuforums.org/showpost.php?p=1189681&postcount=105)

At this point I'm not sure if my settings are causing the connectivity problem or if I just haven't configured everything correctly. Any help would be appreciated.

---

### Post by CasPol on 2007-12-31
Hi there;

I have been having similar problems. In fact it took me weeks to get the Broadcom working. It was far more simple then I thought, and I wish I new it before.

To revert your Gutsy install, simply reboot from the cd or dvd and reinstall completely. 

To get the broadcom card up and running:

When at the very end of the re-install of Ubuntu connect the HP Pavillion to the router with an ethernet cable, before you reboot.(keep the disk at hand...)  Now reboot and follow the instructions. The required drivers will be installed from their respective sources, and all shoud work.

After many weeks of trying this worked for me...

Good luck !!

---

### Post by rustybronco on 2007-12-31
Fire up a live cd and try this. [http://ubuntuforums.org/showpost.php?p=3749742&postcount=4](http://ubuntuforums.org/showpost.php?p=3749742&postcount=4)
It was a bcm4318 v2 chipset in a pcmcia nic.

---

