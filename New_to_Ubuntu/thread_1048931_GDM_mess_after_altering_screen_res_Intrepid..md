---
title: "GDM mess after altering screen res Intrepid."
date: 2009-01-24
forum: New to Ubuntu
---

### Post by MichaelSM on 2009-01-24
Long time no visit! Seemed AOK til today ...!

Ubuntu 8.10. New install. Nvidia drivers.

The screen res was default which was too low for my wide-screen. So I ran sudo dpkg-reconfigure -phigh xserver-xorg which gave me more options. Tried 1400x1050 (?) not good enough. Went to the top 1600x1400 or something. Too high. Hmm. 1600x1050 3:2. I'll try that....

Everything went mad for a second, then I wound up with three desktops each overlaying each other. I don't know what to do to fix it.

Just for fun I re-booted using the live CD, and it went straight to the highest res. Well alright, I'll try THIS, and hit the 1600x1050 3:2 option. Same carnage, but after re-booting the live CD, all was back to normal....

So, back to my installed Intrepid with the layered desktops.

I had a look at Recovery Mode and ran all the options there. No change. I ran sudo dpkg-reconfigure -phigh xserver-xorg again expecting it to be pointless, and I was right.

Next step was Cntrl-Alt-F1 and I was hoping to delete some screen resolutions just to get a working desktop. gksudo gedit /etc/X11/xorg.conf was a suggestion I'd read. But there was a comment about gtk and it couldn't or wouldn't open the file.

Any proposals/solutions greatly appreciated.

Thanks everyone,

Mike.

---

### Post by dnRoyston on 2009-01-24
if you're not running X, and you're at a terminal, you should not use gksudo, let along gedit. This is because you are not running graphically. The correct command you should use is:
```
sudo nano /etc/X11/xorg.conf
```

But DO NOT RUN THAT without running this first:
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
If the second code above doesn't work (with a "Permission Denied" error), then simply add sudo at the beginning of it.

This is only how to get to where you can edit xorg.conf. As for editing it, someone else will have to help with that, because I have horrible luck with it. :\

---

### Post by Crafty Kisses on 2009-01-24
I need a little bit more information then what's already provided, what are your full system specs? I'd also like to see your X, please post the results of this command:
```
sudo nano /etc/X11/xorg.conf
```
You could always try and fetch the latest nVidia drivers from nVidia's website and see if you get any different results.

---

### Post by dnRoyston on 2009-01-24
This man will help you, as he has a bird for his avatar.

---

### Post by MichaelSM on 2009-01-24
Thanks for the fast action!

OK. Re. system: Ubuntu 8,10, kernel 2.6.27-9-generic

Old 1.8 Celeron PC. 1.3G RAM. Nvidia GeForce 5500 256 AGP card.

I did this install yesterday and downloaded all the upgrades from Ubuntu, plus got all the latest drivers from Nvidia.

All was perfect util I hit the 1600x1050 (?) 3:2 screen res.

Why was it different with the Live CD?

BTW I entered the backup command, then sudo nano /etc/X11/xorg.conf which got me into a place where I couldn't find any screen res entries. Wrong file?

Can you see what I'm trying to do? As in edit out most of the higher  screen res options esp the trouble-maker, reboot into a low res, then sudo dpkg-reconfigure -phigh xserver-xorg which should reset everything, and choose the screen res I need, any one EXCEPT for the dodgy one.

Sorry about the long spiel. I just try to explain things clearly.

Looking forward to assists!

Cheers,

Mike.

---

### Post by MichaelSM on 2009-01-24
OK looks like fixed.

Booted into Recovery Mode. Waited for Options screen. Selected root shell.

sudo nvidia-xconfig

Probably didn't require 'sudo.' 

Mike.

---

