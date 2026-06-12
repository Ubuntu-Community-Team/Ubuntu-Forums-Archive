---
title: "ndiswrapper installedmy  drivers, but it still doesnot perceive wireless internet"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by thesnappysneezer on 2011-01-05
Actually I have done this in both 64 and 32 now, and now I got it and it recognizes the drive and installs it but does not go online, recognize wireless connections in the vicinity and also in the 32 I have a hang up. It installed the drivers from Vista 32 in 32 and Vista 64 in 64 but sinc it would not go online I tried the XP one in 32 and it couldn't install and is no longer responding, the Wireless Network Drivers, no matter how many times I try to access it. Only solution IK have is to rewrite the harddrive yet again, is it bad to do that so frequently?

Am I missing a step? Is there something I need to do after I havethe drivers installed?
Anyways my driver is wua2340 dlink and now I am considering getting a pci card, of which locally available from places I know to get them is only a NetGear RangeMaster Wireless N Desktop according to the Best Buy rep over the phone. I'd rather stick with what I have but hey you anyone, know something that will just work with this? Properly like? Also as an aside, which is better 64 or 32? or at least more functional?

A side note the mouse keeps going out in the64bit., usb mouse

---

### Post by wep940 on 2011-01-06
(1) They must be Windows XP drivers
 
(2) They must match your Linux OS type - 32 or 64 bit
 
(3) Whenever you decide to try another driver, ALWAYS remove the old one first from ndiswrapper -> sudo ndiswrapper -l (loer case "L"), sudo ndiswrapper -e xxxxx where xxxxx is the driver/device returned in the -l command. You must be back to a clean point before trying again.
 
(4) Install ndisgtk and use it. It's a graphical front-end to ndiswrapper and takes away typing a bunch of crap in the command line with the chance of error. If you don't have a net connection, it's on the LiveCD in the /pool/main/n/ndisgtk folder.
 
(5) right-click on network manager and be sure "enable Wireless" is enabled.

---

### Post by scheuri on 2011-01-06
6) If that fails, check the hardware database from ubuntu and get yourself a usb-wireless-stick that (should) work!


Yes, I just did it. I just said, that linux (or ubuntu) is not perfect.
Fact is: wireless is one of the things that can still be very very very very tricky to get running if your device is not detected and there are no drivers for your device by default.
Ubuntu claims (and I do mostly agree) to have one of the best hardware support and...if Ubuntu does not recognize your wireless card, then chances are it will not work.

So, in conclusion:
If your attempt to make it run with ndiswrapper (which could work, I not saying they will not ever) should fail, you might still give it a try searching at google for someone who has the same wireless chip and the same issue as you (and maybe found a solution).
Otherwise I would suggest you check the hardware database and get a (usually not that expensive) wireless-usb-stick and work with that...unless, of course, you want to tinker.

good luck
cheers
scheuri

---

### Post by thesnappysneezer on 2011-01-06
hey Ive done that already some people have gotten m y type running. This will not load the driver for xp, the 32 xp will not load it and I do not seem tp have one for xp 64.

oh I have ndisgtk, it was there all along but I was getting terminal advice, ndisgtk installed drivers for vista but error'd for xp and made th 32 ndisgtk not work at all.

---

### Post by wep940 on 2011-01-07
(1) If ndisgtk error'd on Vista drivers, it's because it can *ONLY* use XP drivers - that's all, no exceptions.  ndisgtk  is just a GUI'd front end to ndiswrapper, so the same rules apply.
 
(2) Be *SURE* to go through both ndisgtk and ndiswrapper command line and remove *ALL* devices/drivers - you need to be back to a clean state.
 
(3) Be *SURE* the XP drivers match your OS type - 32 bit for 32 bit Ubuntu, 64 bit for 64 bit Ubuntu - no exceptions there either.
 
(4) Be *SURE* you have the correct driver files for your adapter - they should be .inf and .sys files.
 
(5) You say your adapter is "wua2340 dlink".  Is that USB or PCI?  If it's USB, please post back the output of lsusb.  If it's PCI, please post back the output of lspci.  We want to make sure you are using the correct driver files for the chipset on your adapter.  This can also help us determine if there is a native driver you can use.
 
(6) Contrary to some opinions, ndiswrapper, particularly when you are smart enough to use ndisgtk as the interface, is really quite simple to use and get adapters running for which there are no native drivers.  It used to be used quite extensively before some of the newer native drivers, but it is also still needed and used by MANY, MANY, MANY people to be able to use their adapters.  Yes, native drivers are preferred.  No, there aren't native drivers for many chipsets.  You see them mentioned a lot here because of the ubiquitous Broadcom series of adapters.  People used ndiswrapper in the past for those, usually following antiquated instructions which made things very difficult.  Things could be done easily if they had asked.  Since there is more support for those chipsets now people want to berate ndiswrapper and tell everyone to use native drivers.  The fact of the matter is that native drivers only exist for a limited number of adapter chipsets.

---

