---
title: "Ubuntu stops working after installing nvidia drivers"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by henchworthy on 2009-07-26
Hi
Just installed ubuntu, looks great!

But i let the updates install all the missing drivers etc on first startup. Then i tried to activate the high graphics settings with the wavey windows etc.
Ubuntu suggested i should install some nvidia drivers in order for the settings to take full effect. Obviously i accepted and it installed the drivers.
Ubuntu then restarted but i get to a command prompt before ubuntu starts up properly and i now dont know what to do.

Any ideas?

Oh im running 
Asus M3N-HD Motherboard
AMD Phenom 9550
2 Gig Corsair DDR2 Ram
2 x XFX 8500 GT but ive only got one activated. SLI will come later.

---

### Post by bailbath on 2009-07-26
It's because you have the two video cards the system needs to know which one to use.
You need to get editing a file from the command line
```
sudo nano /etc/X11/xorg.conf
```
On my system I add 
```
Busid      "PCI:1:0:0"
```
 here is my xorg.conf note under Device section I have added the above code.
> # This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
        Busid   "PCI:1:0:0"
EndSection

After you have added it to save ctrl-x on your keyboard.

---

### Post by henchworthy on 2009-07-26
Thanks for the help. I ended up taking the other card out and now ubuntu strikes up fine.

---

### Post by bailbath on 2009-07-27
Well thats another way to do it! I don't think it makes a difference to the performance anyway!
If you decide to put the card back in you got the solution above to follow.
Ian

---

