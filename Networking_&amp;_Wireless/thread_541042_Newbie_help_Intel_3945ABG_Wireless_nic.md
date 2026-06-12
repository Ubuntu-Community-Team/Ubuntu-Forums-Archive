---
title: "Newbie help Intel 3945ABG Wireless nic"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by lbriner on 2007-09-02
A friend installed a fresh copy of Feisty 64bit onto my new Samsung Q70 laptop. It comes with a 3945ABG Intel wireless card. During the install he said that the system couldn't identify the wireless card so I have a system which seems otherwise complete but minus wireless (although installing the NVidia driver was a pain in the chuds!). This is strange because the forums imply that the wireless card is supported out of the box but not for me. I looked on the Intel site but their download and install instructions are horrifically complicated and not something I want to do being a newbie. I'm not sure how to install a card in Linux, assume if I have the right modules installed then it will work but can't find any help. Can someone please advise me.

Luke

p.s. The network card is displayed on lspci as an unknown Intel Network controller.

---

### Post by noob12 on 2007-09-02
Have you tried the 32-bit installation?  

Posting the actual lspci output would help.

If you do have the 3945 card, you should make sure the card is enabled in the Restricted Drivers Manager ( System | Administration | Restricted Drivers Manager ).
You can verify if you have the module installed at all by typing **modinfo ipw3945**.

---

### Post by lbriner on 2007-09-03
I couldn't find System - Administration etc, I am using KDE, is that a Gnome thing you suggested?

The relevant output from lspci is:

```
02:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
```

Typing the modinfo line gave me loads of info about the ipw3945 module as expected so no probs there?

---

### Post by noob12 on 2007-09-03
OK.  Well that means you have the ipw3945 module.  However from the lspci output we now know that you don't have an Intel 3945.  Your wireless device is actually an Intel 4965.  That's why the 3945 driver isn't claiming the device.   You need to install a driver for the 4965.

I have to go but I or others will help with this.

ADDED:  

Your options are basically these:
- Ubuntu Gutsy Tribe 4 and later is rumored to have support built-in.  That's a pre-release and you may not want brave those waters yet.
  (Rumor source was [http://ubuntuforums.org/showthread.php?p=3132859](http://ubuntuforums.org/showthread.php?p=3132859)).
- You can try to download, build, and install the drivers from here: [http://ubuntuforums.org/showthread.php?p=3132859](http://ubuntuforums.org/showthread.php?p=3132859) .  I haven't done this for these drivers so I'm not very well prepared to guide you.
- You can try following this thread, but it is already somewhat dated; you might try pinging the author for help: [http://ubuntuforums.org/showthread.php?t=493095](http://ubuntuforums.org/showthread.php?t=493095)
- You can use ndiswrapper and the Windows driver.
- Someone else on the forum may have a better tip.

---

### Post by lbriner on 2007-09-07
Thanks for the help. You were right of course. Unfortunately the card only seems to be supported in the Gutsy kernel so had to obtain the new kernel and run it in Feisty. I used the following VERY helpful thread:

[http://ubuntuforums.org/showthread.php?t=493095]("http://ubuntuforums.org/showthread.php?t=493095")

This let me download the parts from the Intel site and rebuild. Unfortunately in the process, because i use the NVidia proprietary drivers, I had to rebuild these for the new Kernel before restarting. The instructions were exactly as described and I don't think I had any problems except not noticing the -s on the ln command line!!

Luke

---

