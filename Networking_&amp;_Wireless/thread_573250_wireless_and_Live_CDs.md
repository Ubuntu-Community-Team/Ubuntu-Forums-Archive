---
title: "wireless and Live CDs"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by SeePU on 2007-10-11
My question is regarding using Live CDs and after installing, what can happen to wireless applications.  

Here's the puzzle:
I originally thought my wireless adapter was a problem for Linux and although it is supported (Zydas and zd1211b chipset, zd1211rw driver), I had problems when trying Kubuntu (initially worked then didn't).   I had an option to use WPA but then somehow lost the option.   I could only manually configure using WEP. 

Okay, to make a long story short, I decide to try Live CDs.   A Live CD of Ubuntu 7.04 Feisty allows me to enter the WPA password and I get wireless!   So, I try Kubuntu Gutsy today and lo and behold, that works (btw, the KNetwork Manager is much improved!!).   

But, what happened to my (Kubuntu) install?   WPA is not an option.   I downloaded Wicd but even though wpa is listed, I still can't get it to work.   I know the obvious answer is to forget about it and install one of the Live Cds.   But, I don't want the same experience.   That's why, I would like to know how KNetwork Manager can break.   Do any of you Ubuntu users have a similar experience?   Do you have any cards or USB adapters that first work out of the box but then suddenly  stop working?   And do you lose any options to configure using WPA?

I might never solve the problem but my suggested solution is to install BOTH Ubuntu and Kubuntu (Live CDs in which wirless worked) and hopefully one of those will keep working.  :-)

In the meantime, I suggest to anyone wanting a *USB* adapter that works in Ubuntu/Kubuntu without too much trouble to consider one with the Zydas zd1211b chipset.   If anyone needs to know which devices have that, just pm me.   I have researched on it so much when I was having problems so I know which ones.   Now, I realize when people are saying it's working, what they mean.   However, do NOTE, that stuff does happen that stops these devices from working as I can confirm.  That is why you read of Linux users having problems while other claim it worked 'right away.'   What needs to be found, imho, is what is happening between the time the device worked and the time in which something 'broke.'   I would prefer to not have to re-install each time the wireless loses options (in configuration).   

Sorry, I didn't mean for this to be so long but I am hoping I can help anybody who is currently frustrated with their usb adapters trying to get Ubuntu to work.   

If you find anything I misread in my experimentation or assessment, please mention it.  I am a newbie but we all make mistakes.  I tried to use the GUI part of the wireless apps as much as possible although I am sure there are methods to get the device to work using the command line using scripts or editing lines.   I didn't want to use ndiswrapper since the device (is obviously) supported and the preference was to see if it would function well enough using the open source support.

Lastly, I would stick to newer distros or more recent kernels (in which, there are newer modules related to the zd1211 in the repositories).   It is more likely for the zydas device to work.  Just my opinion, though... YMMV.   I noticed the repositories have more files for the rt2400/2500 chipsets now, too.

---

