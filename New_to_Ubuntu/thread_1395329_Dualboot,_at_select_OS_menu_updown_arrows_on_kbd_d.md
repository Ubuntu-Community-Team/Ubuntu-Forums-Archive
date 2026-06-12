---
title: "Dualboot, at select OS menu up/down arrows on kbd don't work.."
date: 2010-01-31
forum: New to Ubuntu
---

### Post by colinmccubbin on 2010-01-31
I just installed winxp and ubuntu 9.10 on a new pc, all works fine, but when the choose os menu appears, with ubuntu as the highlighted default, Windows is the last menu item but my keyboard's up/down arrows don't move the highlighting down and I can't do anything but watch the timer count down and ubuntu starting!  So I can't boot into windows.:p

Once ubuntu is 'up' all the keys on my kbd work fine, just not at the boot menu. 

USB keyboard and mouse btw.

Any thoughts please? (I'm not a techie, but believe that the usb ports and thus the keyboard/mouse are enabled in the bios startup so aren't waiting for an os to load?)

---

### Post by candtalan on 2010-01-31
I have just had the same problem after replacing an older mainboard with a newer one of a different type. I was using an old - very old - ps2 keyboard, which was no problem in the old system. However, this keyboard did not work with the new system, but a newer keyboard, still ps2, worked ok. I decided that the newer mainboard used less powerful circuits or something, maybe even different pins in the keyboard ps2 plug. Anyway, I now keep the older keboard to use with the older systems....

good luck

---

### Post by colinmccubbin on 2010-02-01
The keyboard I was using, was quite an old, complex one, with music player controls, etc meant for windoze, I tried a newer, basic USB keyboard and it worked, I can move up/down the os select menu, but only in the last few seconds before it counts to 0.

I think that there was a 20 sec countdown with 8.10 but notice it is only 10 secs now with my new 9.10 install. Is there a place where I can change the default countdown time since I suspect that the 10 secs is too short for my old keyboard to properly be initialised.

---

### Post by oldfred on 2010-02-01
The setting is here:

gksudo gedit /etc/default/grub

and your have to run this afterwards to write it into grub.cfg
sudo update-grub 

More info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Herman's pages on Grub2
[http://members.iinet.net/~herman546/p20.html]("http://members.iinet.net/%7Eherman546/p20.html")
GRUB 2: A Guide for Users 
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

---

### Post by Ebonhawke on 2010-02-02
Another possibility is to look at the BIOS.  Under 'Integrated Peripherals' there is an option to Enable/Disable Legacy support of USB keyboards.  I had the same problem with not being able to use the keyboard/mouse at the menu (and just had to wait on the prompt to auto boot).  If I enable the Legacy support, then the keyboard works on the menu :)

---

### Post by eeezzzeee on 2010-02-03
I have been having the same problem. I just replaced my OLD keyboard with a usb keyboard and cannot move up/down in the grub menu. I have tried to enable legacy usb support, but when I do that grub never loads. I just get a black screen with an underscore/cursor prompt and it hangs there, never going to the grub menu. I can only get to the grub menu when legacy support is turned off. Any Ideas?

---

### Post by colinmccubbin on 2010-02-04
> **oldfred said:**
> The setting is here:

gksudo gedit /etc/default/grub

and your have to run this afterwards to write it into grub.cfg
sudo update-grub 


Thank you!

Did that, I changed the line: GRUB_TIMEOUT=10 to GRUB_TIMEOUT=20 and wrote it into grub.cfc and now the menu stays on screen counting down for 20 secs. My keyboard seems to come active after about 7 seconds so at sec 13 the arrow up/down keys now work.

I wonder who made the decision to cut the timer from 20 secs (default in 8.10) to 10secs in 9.10? This must be causing aggravation to loads of folk who have upgraded.

Do you remember the old Byte Magazine, and Jerry Pournell's maxim "if it ain't broke, don't 'fix' it"....

---

