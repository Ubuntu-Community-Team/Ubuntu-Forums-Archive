---
title: "[SOLVED] Wireless Issues"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by maretard on 2008-06-17
Yeah, yeah, I know, JFGI. Unfortunately, I have, and I've tried numerous solutions, all which have not worked. I'm stumped. T_T

My card is as follows: Broadcom BCM4318 AirForce One 54g rev 02.
Yes, I did set up ndisgtk, and I got my driver in .inf format, and I did the following:

sudo gedit /etc/modprobe.d/blacklist
Found an empty line, entered: blacklist bcm43xx (to disable current drivers)
[reboot]
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m

Unfortunately, this still didn't work; it said I already had the drivers installed. So I uninstalled my driver with -e, and then installed it again, and it installed and said everything was a-ok, except... I still couldn't connect to a network.

I tried:
sudo ndiswrapper -l
And it gave me the driver, BCMWL15, but said right next to it, "Invalid Driver!", which makes no sense since this was undoubtedly the driver for my card. Now, for some reason, the little network icon in the top-left corner doesn't even display anymore, and all I have is my username, volume controls, and the time.

What on earth is going on here?!?
And what am I supposed to do to get this stupid old wireless card to work with Ubuntu??? T_T

---

### Post by ago on 2008-06-18
Hi you might want to move this on the networking forum:

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

---

### Post by maretard on 2008-06-18
Ah, never mind, problem solved. :D
Apparently I had 169 updates to various parts of Ubuntu that I hadn't installed yet. -_-"
As soon as I did, it told me I had restricted drivers available for my Broadcom card, whereas before it only showed my ATI graphics driver. Installed those, and now it works perfectly. :)

---

