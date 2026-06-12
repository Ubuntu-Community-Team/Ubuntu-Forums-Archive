---
title: "New to Ubuntu, font issues...troubleshooting help needed"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by Tj218 on 2009-04-24
Relatively new to Ubuntu (less than a couple weeks) and have some questions.

I installed 9.04 on a different computer than had it before and am noticing some issues can anyone help me diagnose the source? 

1. Fonts are displaying weird, some letters may have gray squares around them (most h's have this), others may be completely disappearing, while any "y" I type is displaying a line through the top and bottom of the  y to make it llok like a roman numeral 1. 

2. Icons for example the home, back, stop on the Firefox toolbar are not displaying correctly either (black squares with some white lines between them.

3. Sometimes the clock seemingly disappears. 

4. Hard drive seems to be accessed too much (when cruising the Internet, it sounds like I am doing serious photo editing)

5. Screen brightness seems to fluctuate from time-to-time.

6. I have to keep entering my WEP key on my wireless connection ( Ihave one of those Atheros chipsets that is now supported out of the box) after every log-in any way to save this?

I have this setup as a dualboot with XP. 
Toshiba Satellite S1000 computer (256 RAM, 1.06Ghz Celeron)
Partition (used in the installer on auto) for Ubuntu is quite small (was only 2gb, I can't even install Firefox updates due to lack of space)

For issues 1-5......My thought is if this related to the small partition and lack of space for swap files etc. Does this sound right? 

 Or is this due to lack of RAM or the old Celeron? Graphics driver? 

 If it is lack of HD space I will just wipe the HD and start fresh, but I am reluctant to do so if it won't solve the problem. 

Thanks for any and all help!

---

### Post by Didius Falco on 2009-04-24
Try this:

Go to System/Preferences/Appearance. When it loads, click the Fonts tab and see if Subpixel Smoothing is enabled - if it isn't, do so. Then click the Details button and set Smoothing to Slight.

---

### Post by kanikilu on 2009-04-24
Several of those things sound video-related. Have you checked to see if any drivers are available? System > Administration > Hardware Drivers (I think, I'm not in Gnome).

Also, can you post more information about your hardware, specifically the display adapter: ```
lspci | grep VGA
```

Regarding the disk activity when browsing, I'm just guessing here, but that could be due to having to reach into swap space if you are out of physical memory. Next time it does that, check the output of **free** (or **free -m** if you want to see the results in megabytes).

Lastly, in the future you might want to break up your questions into individual threads so that people can try to help with one thing at a time. Plus, then you can make the subjects more descriptive.

---

### Post by Tj218 on 2009-04-24
> **kanikilu said:**
> Several of those things sound video-related. Have you checked to see if any drivers are available? System > Administration > Hardware Drivers (I think, I'm not in Gnome).

Also, can you post more information about your hardware, specifically the display adapter: ```
lspci | grep VGA
```Regarding the disk activity when browsing, I'm just guessing here, but that could be due to having to reach into swap space if you are out of physical memory. Next time it does that, check the output of **free** (or **free -m** if you want to see the results in megabytes).

Lastly, in the future you might want to break up your questions into individual threads so that people can try to help with one thing at a time. Plus, then you can make the subjects more descriptive.

The subpixel smoothing was already on those settings...

The result of of the lspci are here: 
VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 03)

I tried searching the Hardware Drivers but the only one that pops up is the madwifi one for the wireless card.

Thanks again!

---

### Post by kanikilu on 2009-04-24
Check out this thread that sounds very similar to your video problem:

[http://bbs.archlinux.org/viewtopic.php?id=61433](http://bbs.archlinux.org/viewtopic.php?id=61433)

---

### Post by LowSky on 2009-04-24
you don't have enough RAM, 512MB would be much better, 1GB is really recommended.

as for number 1, go to system, preferences. appearance.
click on fonts and change the rendering.

the fix for 5, go to system, preferences power management, turn off dim screen option

now for 6 go to home folder, show the hidden folders (ctrl+h), got to .gnome2/keyrings, delete default keyring, log out, log back in, when the ask for password for wifi, leave blank, click yes to knowing about it being insecure, and no more password for wifi

---

### Post by Tj218 on 2009-04-24
> **kanikilu said:**
> Check out this thread that sounds very similar to your video problem:

[http://bbs.archlinux.org/viewtopic.php?id=61433](http://bbs.archlinux.org/viewtopic.php?id=61433)



That did fix the font issue, but with that addition to the xorg.conf file now I am having different graphic problems. 

When I surf the net, or am working in a .doc,whenI  scroll down on the top of the in this casewebpage stays on the screen and just part of the bottom moves, likewise if I scroll up the bottom seems to stay as-is but the top moves....

Any thoughts on this? 

Thanks for all your help!

---

