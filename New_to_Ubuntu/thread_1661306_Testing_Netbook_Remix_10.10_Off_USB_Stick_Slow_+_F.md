---
title: "Testing Netbook Remix 10.10 Off USB Stick: Slow + Freezing"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by dmoench on 2011-01-06
[FONT=Arial][SIZE=2][COLOR=black]Hi All,[/COLOR]

[/SIZE][/FONT]      [FONT=Arial][SIZE=2][COLOR=black]I’m trying Linux for the first time and[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2] have some questions.[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial][SIZE=2][U][COLOR=black]
Situation:[/COLOR][/U][/SIZE][/FONT][INDENT][FONT=Arial][SIZE=2] [COLOR=black]I am testing out Ubuntu Netbook Remix 10.10 by booting off of a FAT32 formatted USB stick on an HP Pavilion dm1z laptop/super-netbook. Ubuntu runs and what I checked so far [FONT=Arial][COLOR=black](wireless + webcam) [/COLOR][/FONT]worked right away. However the whole system runs MUCH slower than the Windows 7 OS that came pre-installed on the laptop. Furthermore, once Ubuntu has been running for a few minutes, especially if I click on a bunch of things quickly, the screen goes black and the system freezes- leaving me to force shut down. I restarted a few times, switching the USB stick to the different ports on the laptop, with the same problem each time.[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][U][COLOR=black]
[/COLOR][/U][/SIZE][/FONT][/INDENT][FONT=Arial][SIZE=2]_[COLOR=black]Questions:[/COLOR]_[/SIZE][/FONT]
[LIST=1]
[*][FONT=Arial][SIZE=2][COLOR=black][FONT=&quot][FONT=Arial]Could this be because booting an OS off a USB stick is inherently slower than off of an internal drive?[/FONT][/FONT][/COLOR][/SIZE][/FONT]
[*][FONT=Arial][SIZE=2][COLOR=black][FONT=&quot][FONT=Arial]Could this be an Ubuntu 10.10-HP Pavilion dm1z incompatibility issue? [/FONT][/FONT][/COLOR][COLOR=black][FONT=&quot][FONT=Arial]If so, would other versions of Ubuntu[/FONT] (10.0[FONT=Arial]4 Netbook Remix, 10.10 Desktop) be worth a shot?[/FONT][/FONT][/COLOR][/SIZE][/FONT]
[*][FONT=Arial][SIZE=2][COLOR=black][FONT=&quot][FONT=Arial]Any other suggestions?[/FONT][/FONT][/COLOR][/SIZE][/FONT]
[/LIST]
            [FONT=Arial][SIZE=2][COLOR=black]Thanks for sharing your brains!

[/COLOR][/SIZE][/FONT]   [FONT=Arial][SIZE=2][COLOR=black]-David[/COLOR][/SIZE][/FONT]

---

### Post by ajgreeny on 2011-01-06
Simple answers to the questions are:-
1.  Yes
2.  Yes
3.  You could try different versions of ubuntu, but all will probably be the same in speed.

Longer answers:-

1.  A usb disk read/write speeds are very much slower than a hard disk, so this slow speed is to be expected.  It is, however, much faster than the live CD alternative most used in the past.

2.  It is possible that the HP netbook is not totally compatible, particularly as it has an AMD graphics card.  When installed and using a proprietary driver, if one is available for that card, it may be much better.  I can not see what wireless chip is included, so that may be a problem, but if it works in live mode, it should be OK when installed.

3.  See the last point, re install vs live use, but as for version of ubuntu, I would personally suggest you use the gnome desktop, particularly if you go for 10.10, rather than the unity desktop.  If you specifically want a netbook desktop, use 10.04; it is much more usable, in my opinion than 10.10.

---

### Post by bodhi.zazen on 2011-01-06
I personally find the netbook edition to be slower then a standard installation , so I use xubuntu (I like xfce) on my netbook.

Crunchbang is an alternate.

---

### Post by ubaidillah on 2011-01-06
> **dmoench said:**
> [FONT=Arial][SIZE=2][COLOR=black]Hi All,[/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=2][COLOR=black]I’m trying Linux for the first time and[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2] have some questions.[/SIZE][/FONT]
 
_[SIZE=2][FONT=Arial][COLOR=black]Situation:[/COLOR][/FONT][/SIZE]_
[INDENT][FONT=Arial][SIZE=2][COLOR=black]I am testing out Ubuntu Netbook Remix 10.10 by booting off of a FAT32 formatted USB stick on an HP Pavilion dm1z laptop/super-netbook. Ubuntu runs and what I checked so far [FONT=Arial][COLOR=black](wireless + webcam) [/COLOR][/FONT]worked right away. However the whole system runs MUCH slower than the Windows 7 OS that came pre-installed on the laptop. Furthermore, once Ubuntu has been running for a few minutes, especially if I click on a bunch of things quickly, the screen goes black and the system freezes- leaving me to force shut down. I restarted a few times, switching the USB stick to the different ports on the laptop, with the same problem each time.[/COLOR][/SIZE][/FONT]
[/INDENT]
[FONT=Arial][SIZE=2]_[COLOR=black]Questions:[/COLOR]_[/SIZE][/FONT][LIST=1]
[*][FONT=Arial][SIZE=2][COLOR=black][FONT=&quot][FONT=Arial]Could this be because booting an OS off a USB stick is inherently slower than off of an internal drive?[/FONT][/FONT][/COLOR][/SIZE][/FONT]
[*][FONT=Arial][SIZE=2][COLOR=black][FONT=&quot][FONT=Arial]Could this be an Ubuntu 10.10-HP Pavilion dm1z incompatibility issue? [/FONT][/FONT][/COLOR][COLOR=black][FONT=&quot][FONT=Arial]If so, would other versions of Ubuntu[/FONT] (10.0[FONT=Arial]4 Netbook Remix, 10.10 Desktop) be worth a shot?[/FONT][/FONT][/COLOR][/SIZE][/FONT]
[*][FONT=Arial][SIZE=2][COLOR=black][FONT=&quot][FONT=Arial]Any other suggestions?[/FONT][/FONT][/COLOR][/SIZE][/FONT]
[/LIST][FONT=Arial][SIZE=2][COLOR=black]Thanks for sharing your brains![/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=2][COLOR=black]-David[/COLOR][/SIZE][/FONT]
 
I would like to say that Yes, Booting from USB stick take more time for me first time running Ubuntu 10.10 Netbook Edition on my Lenovo S10-3.
 
Cheers

---

### Post by dmoench on 2011-01-07
Thanks all for the feedback.

Last night I tested Ubuntu Desktop 10.10 off of the USB stick and it ran very smoothly and no longer had the previously mentioned freezing issue. I decided to install the OS on the system drive.

However, when I go through the installer steps I get stuck on the "Preparing to install Ubuntu" step (see attached picture). When I click "Forward" the mouse pointer switches to the rolling-circle/thinking icon and it never goes on to the next step. It doesn't seem to be frozen because I can still select and deselect the "Download updates" and "Install third-party software" options and quit the installer. I let it run all night- this morning nothing had changed, it was still thinking but not frozen.

Any ideas?

Thanks!

---

### Post by castlefox on 2011-01-17
From what I have been reading there has been issues using Fusion and the latest Ubuntu releases (other linux distro's for that matter)  I would suggest going to 11.04 as soon as it is released for better support. 


I would suggest plugging in an Ethernet cable, Ubuntu might be having some issues the WIFI card without being able to download some info from cloud. 


PS> What do you think of the touch pad and buttons?  I was thinking about picking that laptop up.

EDIT> Im rather sure the fusion update will be in the 2.6.38.  2.6.38 will not be in 11.04, so I guess we just have to wait till 11.10

---

### Post by bjje on 2011-02-24
I am testing Netbook remix 10.10 off of a USB stick made with unetbootin and on startup I get an error 
"No required driver detected for unity" then it loads gnome, works normally.
Unity stuff seems to all be installed, what am I missing?

---

### Post by t0adman on 2011-03-14
> **castlefox said:**
> From what I have been reading there has been issues using Fusion and the latest Ubuntu releases (other linux distro's for that matter)  I would suggest going to 11.04 as soon as it is released for better support. 


I would suggest plugging in an Ethernet cable, Ubuntu might be having some issues the WIFI card without being able to download some info from cloud. 


PS> What do you think of the touch pad and buttons?  I was thinking about picking that laptop up.

EDIT> Im rather sure the fusion update will be in the 2.6.38.  2.6.38 will not be in 11.04, so I guess we just have to wait till 11.10

I'm installing Desktop 10.10 64-bit now and the touchpad is brutal.  You can't click/hold and try to drag the windows or it flies around the screen.  You can depress the middle of the touchpad and slide your finger but that's limited although does work.  

I'm currently trying to get my Logitech bluetooth travel mouse to connect (as it's done in the past with 10.10) and it won't show up while discovering devices.  Strange.

---

### Post by I2k4 on 2011-03-15
If you are still version shopping, I suggest running systems from a 4GB USBdrive with 2GB of "Persistence" to save settings between boots.  I'm using Lubuntu 10.10 on a 2GB USBdrive on my first-gen Acer netbook very successfully right now.

The USBdrive is slower, but as such is a good test of responsiveness for different versions, and there's no fear of mucking up the hard drive with an install you come to regret.  (I tested the Netbook remix after Ubuntu Desktop and immediately noticed what a dog it is.)  In particular, I'm looking forward to trying out the new 11.04 in a couple of months, so am holding off any decisions about dual boot (XP) from the hard drive before then.

---

