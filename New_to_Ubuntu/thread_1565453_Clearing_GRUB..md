---
title: "Clearing GRUB."
date: 2010-08-31
forum: New to Ubuntu
---

### Post by blucalvin on 2010-08-31
Hi.
I'm having trouble editing the GRUB menu after installing ubuntu 10.04 lucid lynx on my lenovo ideapad.
It seems to be different from the 9.04 releases in its GRUB features as I can't find the menu.lst.
How can I edit my GRUB menu?

Cheers.

---

### Post by alphacrucis2 on 2010-08-31
> **blucalvin said:**
> Hi.
I'm having trouble editing the GRUB menu after installing ubuntu 10.04 lucid lynx on my lenovo ideapad.
It seems to be different from the 9.04 releases in its GRUB features as I can't find the menu.lst.
How can I edit my GRUB menu?

Cheers.

It will be grub2 which doesn't have a menu.lst. 

[URL="https://help.ubuntu.com/community/Grub2"]Some info here....
[/URL]

---

### Post by oldfred on 2010-08-31
More links
General info:
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

If you really want to customize:
Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

How to: Create a Customized GRUB2 Screen that is Maintenance Free. 
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

Partial Custom:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes lines to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

---

### Post by andrewthomas on 2010-08-31
and another 
the grub2 guide
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

