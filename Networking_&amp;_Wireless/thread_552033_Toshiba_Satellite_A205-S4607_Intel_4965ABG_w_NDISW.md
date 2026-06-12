---
title: "Toshiba Satellite A205-S4607 Intel 4965A/B/G w/ NDISWRAPPER - COMPLETE"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by rast4man on 2007-09-15
So I had my sound and wifi working fine on a 7.04 install, then something random happened one day and I had to do a new install. I did what I thought was the exact same method I used last time in order to get the wifi to work, but I hadn't.

This brief post just introduces an easy way to do it in 7.04.

The following post by this user made this all clear:

> **fredj said:**
> What version of ndiswrapper are you using. The version in the Feisty repositories does not work. It is the
wrong version. Open a terminal and type ndiswrapper -v and post the result here. If there is any suggestion 
of an error in the message you get then you probably have the faulty version. 

The only way to get a good version is to download the latest source files from the ndiswrapper site and
compile them. I know because I have been through all this. The wrong version was put in the Feisty 
repositories and now it can't be corrected. The whole thing is very frustrating and needs to be given wider
publicity so people don't waste their time with a program that just doesn't work.

Start fresh with an Ndiswrapper install. If you have a previous version (prior to 1.47) then issue this command to uninstall (keep running the command until it stops comlpaining) : sudo make uninstall

After the "errors" are gone from the above command, proceed to compile your Ndiswrapper. (NOTE* I assume you have all of your compiler/make/gcc/etc installed and working properly) Download the newest version here 

Follow the instructions on the Ndiswrapper install page here: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

The drivers that worked are the same ones I used before, and everyone else for that matter. V11.1.1.0_XP_DRIVERS Within that file, the NETw4x32.INF is the one which works with Ndiswrapper.

Here's where I fouled up last time. Keep the physical wifi switch off BEFORE you install the version of Ndiswrapper. When you are finished, click on Knetworkmanager and disable wireless. Reboot the computer leaving the switch off until you get into KDE/Gnome desktop. Switch the physical wifi switch on and then open Knetworkmanager and enable wireless. Within 30 seconds or so the networks should come up. 

I did this twice, reversing everything I did and did it again in order to ensure that what I'm typing is ok. Happily, I'm typing this on my Intel 4965A/G/N card wrapped by Ndiswrapper. :)

Hope it helps someone, if not maybe it will still be here in case I forget. :)

---

