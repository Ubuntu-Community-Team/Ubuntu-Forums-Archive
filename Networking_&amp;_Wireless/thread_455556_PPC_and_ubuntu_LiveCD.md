---
title: "PPC and ubuntu LiveCD"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by Ryupower on 2007-05-26
Hi, I have someone who was trying to test the ubuntu Feisty Fawn LiveCD. He used an ibook G4 , but he said the wireless wasn't working, he couldn't go online. 

Anyone here know what he could be doing wrong? He said that the wireless card goes on automatically and there's no button on the computer or it's keyboard to turn it on/off, so he wouldn't be able to turn it on during boot. The description of the LiveCD even listed G4 as an example.

---

### Post by tcrroadie on 2007-05-27
Hi Ryupower,

The airport card in your friends ibook will work, but a tool called bcm43x-fmcutter needs to be installed first.  bcm43x-fmcutter is a tool that will extract the firmware for the airport wireless card from the OS X installation.  I am not sure if this can be completely done when using the live cd, since the Mac OS X installation needs to me mounted in order to extract the firmware from it.  But after installation of Ubuntu, it is a breeze.  bcm43x-fmcutter can easily be installed using apt. 
```

sudo aptitude install bcm43xx-fmcutter
```

If your friend is really gung hoe about using Ubuntu Feisty on his ibook, I would recommend just installing it.  An Ubuntu installation uses less than 2.5gb of disk space and it is very easy to set up the ibook to dual boot OS X and Ubuntu Feisty.  A reinstallation of OS X will be needed though.  

Let us know if you need any help.  I am also an Apple ibook G4 user.  Wireless works great on my ibook with Feisty.

---

