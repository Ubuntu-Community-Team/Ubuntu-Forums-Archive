---
title: "Disable ATI Driver in 9.04"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by fly360 on 2009-07-08
Does anyone know how to disable the ATI driver so I can get this OS to boot? I've tried the original disk but I'm unable to do anything unless it is in the Demo mode. Without the disk it boots to a scrambled screen with smaller Ubuntu icons and freezes there.
I don't want to reinstall the os because other than the driver I had it perfect. It was doing everything that I like.

---

### Post by cozmicharlie on 2009-07-08
These instructions should help [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide).  Go to the bottom of the page and it has instructions for removing the drivers.  You will need to drop down to a shell when logging in.  In the grub menu, go to safe method when booting and it gives you an option to go into a shell then follow the instructions.  You can also try to fix this (I had the same problem and I used the "fix graphics" and it allowed me to boot back in the system.  I have never been able to get the ATI drivers to work from the Ubuntu "add hardware".  I have always had to add the drivers via the manual method.  

When installed correctly, the ATI drivers really do work good (in fact in my system they work better than in Windows).  If you want to give it another shot once you uninstall the drivers, this is what I do:
[LIST=1]
[*]Install Ubuntu Tweak ([http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)).  This is a great program for doing lots of tweaks in Ubuntu very simply.
[*]Once installed, start UT from applications>system tools and go to applications>third party. Unlock and mark the sources for "ubuntu X" and do an upgrade (system>update manager).
[*]Install the ATI drivers using the manual method
[/LIST]

This should give you working ATI drivers.

Hope this helps.

---

### Post by kandieyman on 2009-07-08
I agree that you will need to uninstall fglrx (the propreitary ATI driver), but I doubt that you will be able to get your card to work with anything other than the opensource driver that is automatically used. Since ATI marked most of its cards as legacy, you probably have one--unless you bought the card in the last few months--that will only use Catalyst 9.3 which is not supported in Ubuntu 9.04.

---

### Post by fly360 on 2009-07-08
Thanks for the replies, I will give it a shot right now.

---

