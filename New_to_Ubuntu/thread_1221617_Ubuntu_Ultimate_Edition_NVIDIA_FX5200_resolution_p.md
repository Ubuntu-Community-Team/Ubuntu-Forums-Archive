---
title: "Ubuntu Ultimate Edition NVIDIA FX5200 resolution problem"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by imtheshade on 2009-07-24
Hi! I installed Ubuntu Ultimate Edition 2.2 and the NVIDIA drivers for it (version 173.x) and when the login screen appears, my resolution is 800x600. After the login is successful, the resolution goes down to 640x480. I tried configuring my resolution from the NVIDIA configuring tool but the max resolution that appears there is 640x480.

Can someone please help me take it up to 1024x768 which is, by the way, supported by my video card and worked in Ultimate Edition 1.4

---

### Post by superprash2003 on 2009-07-24
go to system->admin->hardware drivers and see if you can enable any nvidia driver

---

### Post by imtheshade on 2009-07-24
I got the version 96 of the driver active and I can't activate/deactivate it from X because the resolution won't paint me the lower part of the window.

---

### Post by superprash2003 on 2009-07-24
try getting the version 180

---

### Post by pirog on 2010-01-30
i know, it is an old post, but ...
I just installed Ultimate 2.5 side by side with Jaunty. I had to install my NVidia driver afresh. It installed alright, even gave me "Extra Visual Effects", but the resolution stuck at 600x480 (with native being 1680x1050). So, I kept re-installing, installing new drivers, I tried everything, including restarting after each fresh install, but to no avail.

So, I had Ultimate removed from HD, then gone back, installed it again and then install the driver for my graph. card. Only this time, after the installation, i did not restart the computer, nor did i restart X, but instead I had my machine to halt:
```
sudo shutdown -h now
```
then cut the current to my computer at the mains, gave it a minute and upon a restart the machine recognised correct resolution settings and I am now playing with a new addition to my Linux family :)

I hope it helps someone in some way ;)

P.S. not sure whether this is a bug or just my particular hardware set-up.

---

### Post by Blackwolf_Oz on 2010-04-08
Ultimate Edition is growing. With more and more users finding the light, the support infrastructure needs to grow – and it has. :rofl:
There is now a choice of 3 different international forums:

[http://forumubuntusoftware.info](http://forumubuntusoftware.info) (Ultimate Edition Central)
[http://www.ultimateeditionoz.com/](http://www.ultimateeditionoz.com/) (Ultimate Edition Australia/Oz)
[http://ultimateeditionisrael.freeforums.org/](http://ultimateeditionisrael.freeforums.org/) (Ultimate Edition Israel)

All three are focused on just one goal – to make your Ultimate Edition experience the best it can be. Join one or join all three, the choice is yours.
For those of you who like to socialise via Facebook:

[http://www.facebook.com/group.php?gid=6](http://www.facebook.com/group.php?gid=6) ... 056&ref=ts

Ultimate Edition – We've got you covered. :great:

Ultimate Edition is like asking for a romantic kiss with the girl next door and being taken to a month long party at the Playboy Mansion. You ask for a few more applications a few more tweaks to get your Ubuntu running a little more smoothly and you get drowned in so much choice, you probably flounder for breath.

This is not necessary good or bad, but I'm sure some people will find the extreme opposite of Ultimate Edition to what the default Ubuntu offers a little frightening. And others will cherish it like rain in the desert.

The choice of included programs is simply phenomenal. The programs are selected with care and a good balance is maintained between different categories and different uses, allowing just about anyone a hefty sample of everything. If you're lazy and want everything served on a platter, Ultimate Edition is the right formula for you.

The price you will have to pay is the reduced performance, much increased system resource usage and occasional application crashes and incompatibilities, as it seems virtually impossible to orchestra this huge install base without glitches.

Overall, Ultimate Edition in an impressive, welcome project. Future versions will offer an even better, more streamlined integration of applications into the distro and seek to reduce the system resource consumption as much as possible.

---

### Post by rulitawyn on 2010-04-22
I am having this problem too please help i am running Ubuntu 9.10 (karmic)the only nvidia driver that is compatible with my card is 96 according to envyng. i have tried several ways of getting my rez above 640x480 and the only way i have found to uninstall the nvidia driver is to enable destop panning set to a higher rez and panning down to the buttons at the bottom of the window

---

### Post by realzippy on 2010-04-22
[http://ubuntuforums.org/showpost.php?p=9158917&postcount=4](http://ubuntuforums.org/showpost.php?p=9158917&postcount=4)

---

