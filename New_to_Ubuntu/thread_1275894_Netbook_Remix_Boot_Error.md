---
title: "Netbook Remix Boot Error"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by Saganist on 2009-09-26
I'm running jaunty netbook remix on an HP mini 5101 and often have problems when booting.  After selecting the UNR boot option (I'm running a dual boot with XP) from the selection menu the system frequently displays multiple lines of text beginning with a number (usually 3.xxx... which I assume is the time since the boot option was selected), one of which contains "unknown boot option".  To get around this I have to manually shut off the system and reboot, sometimes 3 or 4 times before Ubuntu will finally run.  Other times Ubuntu starts on the first try.  Can anyone give me some advice on what might be going on here and how to fix it?

Edit:
When first installing from a USB drive the same problem would occur after the first time I booted from the USB drive.  That is I was able to boot from the USB drive once without error but was never able to shut down the system and then boot from the USB drive again (seemingly no matter how many times I rebooted).  I had to remove everything from the drive and remount the image in order to boot from the memory key again.  I've also tried reformatting the hard drive and reinstalling Ubuntu in order to fix the problem without any success.

---

### Post by bodhi.zazen on 2009-09-26
As difficult as it may be , it would help if you can post the exact error message.

Sounds as if you need to configure GRUB, but that is just a guess.

---

### Post by Darkwing-Duck on 2009-09-28
You can try to restore grub and see if that fixes your problem. Try this guide.

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

If that doesn't work however, and from the bottom half of your post you may want to try to remake your USB LiveCD again and try it over. There may have been errors from the disk to the install.

One of those should be able to help you out.

---

### Post by BiQ on 2009-10-11
Hello, I am also having a boot problem on my HP mini 5101... I have to try booting usually 2-5 times before I actually manage to get to the ubuntu splash after selecting ubuntu from grub... here are some screenshots: [http://www.cs.helsinki.fi/u/ttuura/bootproblem/](http://www.cs.helsinki.fi/u/ttuura/bootproblem/)

An acquaintaince linux admin guessed that it might be worth filing as a driver/kernel bug... what do you guys think?

About the drivers, this one does have a Broadcom 43224AG 802.11a/b/g/n-draft WiFi-adapter which ubuntu's management software claimed to have only closed-source binary drivers... I hope it doesn't translate into unresolvable problem... :( I'd really like to use ubuntu instead of windows xp...

---

### Post by BiQ on 2009-10-14
Well, you know what? My problem seems to be solved by installing the 9.10 Karmic koala beta. (or was it alpha?) :) It's also quite a bit sleeker:guitar:

---

