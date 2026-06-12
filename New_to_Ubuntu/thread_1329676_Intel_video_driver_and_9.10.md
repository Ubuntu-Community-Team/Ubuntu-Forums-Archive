---
title: "Intel video driver and 9.10"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by Geekboy on 2009-11-17
I'm having an issue with my video driver.  I'm running a fresh install of 9.10, but the problem appeared with an 9.04 to 9.10 upgrade.   All my graphics are very dark.  My video card is a onboard Intel 82945G chipset.  I believe in previous versions I just switched to the Vesa driver.

Is there any way to fix this?  All graphics and images are very very dark.  How can I set it to just use the Vesa driver?

Thanks for your help.

---

### Post by Jon Monreal on 2009-11-17
> **Geekboy said:**
> I'm having an issue with my video driver.  I'm running a fresh install of 9.10, but the problem appeared with an 9.04 to 9.10 upgrade.   All my graphics are very dark.  My video card is a onboard Intel 82945G chipset.  I believe in previous versions I just switched to the Vesa driver.

Is there any way to fix this?  All graphics and images are very very dark.  How can I set it to just use the Vesa driver?

Thanks for your help.

I don't mean to sound mean in saying this, but have you checked to make sure your brightness is up?

In the meanwhile, I'll look to see if I can dig anything up on your chipset.

---

### Post by Geekboy on 2009-11-17
No worries.  The first thing I tried was adjusting the brightness.  Its not that.  It was fine for 9.04.  But turned dark*fter I upgraded.  I did a fresh install and the result is the same.

---

### Post by Jon Monreal on 2009-11-17
> **Geekboy said:**
> No worries.  The first thing I tried was adjusting the brightness.  Its not that.  It was fine for 9.04.  But turned dark*fter I upgraded.  I did a fresh install and the result is the same.

This is a shot in the dark, but try typing "sudo apt-get install xserver-xorg-video-intel" into a terminal and pressing enter. I'll continue looking around, however, to see if I can dig up anything else.

EDIT: Can you also go to System -> Preferneces -> Power Management and see if "Dim display when idle" is on in the "On AC Power" and/or "On Batter Power" tabs?

---

### Post by Geekboy on 2009-11-18
xserver-xorg-video-intel is already installed.  Is there a way I can switch to Vesa?  I would but isn't xorg.conf gone with 9.10?

I don't see Dim display when idle, only put display to sleep.  That's set for 10.  

What's weird is that the display isn't dark.  It's just for images and pics.  It's like the colors are off.  And I've done nothing to the Monitor.

---

### Post by falconindy on 2009-11-18
Have you tried enabling KMS?

[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

### Post by garvinrick4 on 2009-11-18
I use same chipset with generic driver and have no problems.
I would not believe it is the problem.

2.6.31-14-generic (#48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009)

Ubuntu 9.10 (karmic)

Intel Corparation 82945G/GZ Integrated Graphics Controller (rev 02)

Intel Corporation 82801 PCI Bridge (rev e1)

Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)

---

### Post by 3rdalbum on 2009-11-18
Quit out of X, and run the command:

sudo Xorg -configure

This should create an Xorg.conf file, and then you can change it to 'vesa'.

---

