---
title: "ATI Graphics Card Not Recognized"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by Kalayzor on 2011-08-14
I just got a HP Pavilion dv7-6175us laptop loaded with Windows 7 Home Premium and decided to install Ubuntu in parallel with it.  I have the following specs:

CPU: Intel Core i5-2410M 2.3 GHz
Graphics card: ATI Radeon HD 6490M Switchable Graphics Card
RAM: 6 GB

I have the additional FLGRX drivers from the "Additional Drivers" tool, but when I try to open the ATI Catalyst Control Center (which I assume to be where I play with driver settings) I get the following as an initialization error:

There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

-----
No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.
-----

Similarly, Ubuntu stopped running Unity since it didn't seem to see that I had a graphics card to run 3D support...so something's up.  I looked into getting a new driver from the ATI website, but all I got was a *.run file, which Ubuntu doesn't recognize.

Long story short -- any suggestions on how I can get my graphics card working in Ubuntu?

Thanks for the help in advance.

---

### Post by waynefoutz on 2011-08-14
Here's the guide to point you in the right direction. 

[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")

---

### Post by Hakunka-Matata on 2011-08-15
System>Preferences>Monitor might get you there

---

### Post by waynefoutz on 2011-08-15
> **Hakunka-Matata said:**
> System>Preferences>Monitor might get you there

If only it were that easy. OP has a hybrid graphics card, linux doesn't have a way, out of the box to enable it. You have to use the "switcharoo" to get it working.

---

### Post by Hakunka-Matata on 2011-08-15
oops, I was thinking simple Radeon, FGLRX

---

### Post by Kalayzor on 2011-08-20
Awesome -- thank you!  I just got back from camp and will give the switcheroo a shot once things settle down.

---

### Post by the_mouse on 2011-10-24
Hey guys, I have a HP Probook 4530s with AMD Radeon 6490M and having the same isuue. I'm using Kubuntu 11.04 and I'm installing the propriety fgrlx driver through the "Additional drivers" application.

The CPU is 2nd-gen i5 and has an integrated video card, so it might have something to do with the ATi driver not properly installing.

I  tried disabling the integrated Intel video card, but it turned out that when fgrlx driver is installed, vga_switcheroo is disabled... 

```
# echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch
bash: /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory

```

Just to check, I removed the ATi fgrlx driver and vga_switcheroo appeared to be enabled, but I wasn't able to turn off the integrated video :(.

Do you have any idea how I could get the fgrlx driver working?


Thanks,
Dimitar

---

