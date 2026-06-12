---
title: "Triple Display with AMD 760G and ATI Radeon HD 4300, 4500"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by correaj on 2010-11-06
I'm somewhat new to Ubuntu using 10.04. I'm learning the commands and enjoying most of what I can get here. However, the only setback is that it doesn't automatically configure all of my video cards. I have and onboard videocard (AMD760G) and the ATI Radean HD 4xxxxx. I have tried everything from the catalyst control to flgx to xserver-xorg-video-radeon/ati but have not acheived all three displays.

Frequently, when i boot up, the onboard connected monitor will show the solid ubunt screen but when it displays the login screen, I get the other two screens from the attached card. At this point the other will go blank and or it will show the blank terminal. Interestingly it will activate when i exit x server with ctrl alt f1. What is the reason for this? Can someone help me configure all three? 

If I have to edit the xorg.conf files, please give me a step by step tutorial or a reference to one. Also, please give me an idea of how to access all the necessary properties of my drivers to put in the xorg.conf file.

Your help is appreciated everyone.

John

---

### Post by Crusty Old Fart on 2010-11-06
Howdy John:

The problem you're having resides in the sad fact that video cards and monitors are now being managed by RandR and Kernel Modesetting (KMS) working together. Unfortunately, the code cats that write RandR have yet to get around to supporting more than one graphics adapter. So, with their current version, you could have two monitors as long as they were driven from the same card. Your kind of screwed trying to run three of them, as I am screwed by running each of my two monitors from separate cards.

I wrote up a tutorial that explains how to have the system generate an X configuration file for you as well as how you can add the Xinerama option to it to extend the desktop across multiple screens. The tutorial addresses dual monitors but it should apply equally to more than two.

A few things worth mentioning are that the method I described may require the use of the default radeon driver that is built into Lucid. It's loaded with options that you'll find in the generated xorg.conf file. I use it to drive both of my ATI 9250's. It's far less buggy than fglrx is. The code cats at Canonical did a good job with it. According to the man page for the default radeon driver (man radeon), it should work for your cards. I have no idea whether or not it will work for the onboard card. It's the only driver that works for my cards because they are so old. Still, it may be worth considering if your proprietary drivers don't get configured as they should in the system generated xorg.conf. Also, if you want to extend your desktop across all three monitors with Xinerama, you can pretty much kiss Compiz goodbye. Xinerama disables it as long as Xinerama is turned on in xorg.conf. The tutorial is pretty easy to follow and even easier to undo if you want to revert back to where you were before trying it. Another thing that happens with Xinerama is that when it is running, RandR won't recognize your screens. That's no big deal because when your system boots and finds a good xorg.conf file in /etc/X11 it takes priority over RandR anyway.

Here's the link to my tutorial:
[http://ubuntuforums.org/showthread.php?t=1611704](http://ubuntuforums.org/showthread.php?t=1611704)

If you run into any trouble with it, I'll be happy to answer any questions I can.

Good luck,

Crusty

---

### Post by phxx on 2010-12-30
Hi Crusty Old Fart,

thanks for the tutorial. I just did my xorg.conf by hand and have Xinerama working with two monitors on two graphiccards. However, it doesn't work for the third monitor on the second card. This screen only displays the clone of the other monitor on the same card.

Here is my xorg.conf:

```
Section "ServerLayout"
	Identifier   "Ian"
	Screen       0 "Screen Left" 0 0
	Screen       1 "Screen Middle" RightOf "Screen Left"
	Screen       2 "Screen Right" RightOf "Screen Middle"
	Option       "Xinerama" "on"
	Option       "Clone" "off"
EndSection

Section "Monitor"
	Identifier  "Monitor Left"
	Option      "DPMS"
EndSection

Section "Monitor"
	Identifier  "Monitor Middle"
	Option      "DPMS"
EndSection

Section "Monitor"
	Identifier  "Monitor Right"
	Option      "DPMS"
EndSection

Section "Device"
	Identifier  "Device Left"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "ATI Radeon HD 4770 [RV740]"
	BusID       "PCI:3:0:0"
	Screen	    0
EndSection

Section "Screen"
	Identifier "Screen Left"
	Device     "Device Left"
	Monitor    "Monitor Left"
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Device"
	Identifier  "Device Middle"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "ATI Radeon HD 4770 [RV740]"
	BusID       "PCI:2:0:0"
	Screen	    0
EndSection

Section "Screen"
	Identifier "Screen Middle"
	Device     "Device Middle"
	Monitor    "Monitor Middle"
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Device"
	Identifier  "Device Right"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "ATI Radeon HD 4770 [RV740]"
	BusID       "PCI:2:0:1"
	Screen	    1
EndSection

Section "Screen"
	Identifier "Screen Right"
	Device     "Device Right"
	Monitor    "Monitor Right"
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

I don't know how to disable the clone and to get another fully working screen. The duplicate screens are "Screen Middle" and "Screen Right" in the xorg.conf.

Like you pointed out in your post, RandR doesn't work here.

Thanks a lot already!

---

