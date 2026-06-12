---
title: "USB Keyboard problem for a Novice user"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by poppemall on 2009-07-28
Hello, I'm having a problem getting my usb keyboard and mouse to work.
[They are both connected using an wireless usb receiver]

The keyboard in question works in GRUB and bios when connected through usb.
When I get to my ubuntu login I can get about one keystroke in *sometimes*, before it flatout doesn't input anything at all. At this point is when I am forced to plug in usb-PS/2 adapters to login and type in the ubuntu OS.

I've been trying hard to use docs and current help threads to solve my Ubuntu problems as I am a new user. This problem has me really stumped though. 

For the record, I somehow messed up the gui a week or two ago; long story short I uninstalled a "cairolib" thinking it was the dock app. This led to booting into a terminal when my pc was turned on.
I used:
```
sudo aptitude install ubuntu-dektop
```
to get it back.

[https://help.ubuntu.com/community/InstallUSBKeyboard]("https://help.ubuntu.com/community/InstallUSBKeyboard")
^This ubuntu doc says: 

"In this case, the principal sources of the problem to be searched in are:

    *

      incorrect o.s. setup files for character mode terminal emulation (e.g. the recovery mode in *ubuntu);
    *

      incorrect window server setup files for graphic windowing environment (when the windowing mode is run, e.g. Xwindow in Linux)"

My question is; Did I mess up these files when I installed the ubuntu desktop again? Or am I missing something?
Thank You in advance.

Specs: Ubuntu Jaunty 64 bit/ Windows 64 bit
EVGA 680i motherboard
Q6600 quadcore cpu
4 Gigs ADATA DDR2 RAM
250GB hard drive
EVGA GTX 260 video card
Keyboard:Microsoft Wireless Comfort Keyboard 1.0A/Mouse:Msoft Wireless Optical Mouse 2.0
/usr,/var,/tmp,/home all have their own separate partitions, if that helps:(

---

