---
title: "Fixed my Intel Pro BG2200 problems"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by melbo on 2008-01-03
First time I installed ubuntu Gutsy, my wifi worked 'out of the box'.  I was happy.
Then it just quit.  No reasons at all.  I tried all the fixes about my wifi button on the front of my Acer Laptop, turning on the radio, restarting the module, etc.  Nothing worked.

Tried to reinstall ubuntu with a fresh format.  Still no-go.

Purchased another Intel BG2200 card and popped it in expecting to fix my burnt out card.  Nothing.  I have worked through all of about 30 different fixes I found online.  Still no go.

Put my old mini pci card back in and did a fresh install of XP, (TinyXP) and bamn!  I had wifi.  Tossed my ubuntu 7.10 gutsy CD back in and did a fresh install of it.  I still have wireless up and running.

This has happened to me twice since I went "all in" with ubuntu and got rid of my dual boot system.  THat's another story as I fully believe that Satan himself created the dualboot and GRUB.....

**How can I save all my current out of the box wireless settings so I can revert to them if/when this happens again?**  And, what causes ubuntu to just drop some settings occasionally with no idiot input? ;)  I'm running fast and fine right now and want to freeze my system just like it is.  Child locks?

---

### Post by patrickfromspain on 2008-01-03
It's probably related to BIOS stuff... for some reason, in Gutsy wireless on my laptop also doesn't work fine: if the card is disabled, although I press the button to turn it on, it won't. THis has worked in all versions since Breezy.... for that reason I moved on to debian testing. By the way, on my laptop, if I turn off the laptop, disconect the power adapter and remove the battery, wireless will start off, in case you could reproduce the problem that way. 

Good luck!

---

### Post by melbo on 2008-01-04
Well, happened again and it seems that it kills the radio after a shutdown/reboot "Hang".
I uninstalled Network manager and went with wicd instead and it seems to be holding the wireless connection just fine.  Evn after a shutdown hang.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

