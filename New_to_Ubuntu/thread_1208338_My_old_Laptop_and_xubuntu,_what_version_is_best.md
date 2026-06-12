---
title: "My old Laptop and xubuntu, what version is best?"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by Znegil on 2009-07-09
First: I am from Germany, so sorry for my bad english.
Hi there, I finally am willing to try a other OS besides Windows.
I wanted to try it on my old Dell Laptop, PIII, 256 MB RAM, Onboard graphic-card (I believe 64 Mb).
two questions:
1. What Version of xubuntu would be faster on my labtop? xubuntu 8 or xubuntu 9?
Is the Version 9 slower because of new features?
2. I know I can try out the system playing it from Live CD. I also heard about "dual boot", that is what I want to have, keep Windows XP for maybe playing some old games on it from time to time and work with xubuntu. Question is, is that "dual boot" a option for installing xubuntu, or do I have to make this in ahead with a different program? Does that work even when I have only on Harddisk in my old laptop?
 
Thanks for any answers ):P
 
Znegil

---

### Post by Paqman on 2009-07-09
> **Znegil said:**
> 
Is the Version 9 slower because of new features?


No, 9.04 is actually faster (certainly it will boot quicker). This is especially so if you specify the new ext4 filesystem when you install.

Another variant of Ubuntu you might want to look into is Crunchbang Linux. It uses a different desktop environment than Xubuntu, and should be more lightweight.

---

### Post by perito on 2009-07-09
Dual boot can easily be done, all you need is space.
Basically you have to create space for xubuntu and install it.
Check this
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Be careful when partitioning, you don't want to formate your old xp.

---

### Post by Paqman on 2009-07-09
> **perito said:**
> 
Be careful when partitioning, you don't want to formate your old xp.

You can also set a dual-boot without partitioning. Just boot up into Windows, pop in the CD and choose the option to install Ubuntu from within Windows. It uses a really simple installer called Wubi that will get Ubuntu set up for your with no hassle.

---

### Post by Hominym on 2009-07-09
A PIII with 256 MB RAM? 

I would forgo Xubuntu altogether and go with [CrunchBang]("http://crunchbanglinux.org/"), which uses the [Openbox]("http://icculus.org/openbox/index.php/Main_Page") window manager, which takes up a lot less RAM. However, Openbox may not be as user-friendly as XFCE, as it requires more configuration, but CrunchBang has good documentation and helpful [forums]("http://crunchbanglinux.org/forums/"). 

If you're still bent on using Xubuntu, I'd go with 9.04, if only for Ext4. Some of the newer services in 9.04 will slow things down, but you can always disable them if you don't need them. 

Dual-booting should be easy enough. GRUB *should* recognize Windows, but if it doesn't, you should read up on editing GRUB's menu.lst.

---

### Post by Ji Ruo on 2009-07-09
I just put Xubuntu 9.04 on a similar laptop (800MHz Celeron, 256Mb ram). It works, but it's pretty slow. The processor is the problem, it can't keep up. I'm pretty sure I used ext3 and not ext4 so that may make a difference.

You will be able to make a dual boot between XP and Ubuntu very easily if XP is already installed. When you get to the partitioning section of the Xubuntu installation CD, the dual boot option will already be selected. It will split the hard drive half XP, half Xubuntu, which will work out fine if it's a 20Gb hard drive.

---

### Post by 1915flyer on 2009-07-09
Before you install, try running a Live CD. 

I have a Dell Inspiron 3700, PIII, 512MB, CD Rom from around 2000 or so. While it will run Ubuntu 8.10, it will absolutely not run 9.04. It won't upgrade, run the Live CD, nor a straight install from the Live CD or the Alternate CD. It crashes nearly every time setting up the Live CD or during an install, usually with segmentation faults or when loading the hardware drivers. I have only gotten through the partitioning process once - with the alternate CD - and while it got all the way to the "Restart Computer" stage at the end, it crashed at the restart.

Try  several Live CD versions of Ubuntu/Xbuntu or other linux to see if it will work and if it is stable before you try an actual install.

---

### Post by Znegil on 2009-07-09
Thanks a lot for the suggestions so far, I will try out xubuntu 8.04 LTS and will see what happens. If not, I may have to search for a smaller userfriendly Linux system. Is [CrunchBang]("http://crunchbanglinux.org/") as easy to handle? What will I be missing if I use that (besides nicer graphics)? Does it have a "Wubi" too?

---

### Post by snowpine on 2009-07-09
Hi Znegil,
I have an old Dell laptop with similar specs (500mhz pentium 3 with 256mb of ram). Xubuntu will DEFINITELY run on those specs, and I highly recommend the current version (9.04).

If compatibility with Ubuntu is your #1 concern, then Xubuntu is your best choice. If speed/performance is your #1 goal, Xubuntu is a poor choice. I switched to SliTaz on my my old Dell, and it is much, much faster than Xubuntu. Other popular "lightweight" options include Debian (with Xfce or LXDE), CrunchBang, Antix, Puppy, DSL, etc.

My advice, if you are trying Linux for the very first time, there is no reason to choose Xubuntu--choose a distro that will run well on your hardware. You will be learning everything from the start anyway, so you might as well learn a distro that will be fast. :) A lot of people on these forums who have bad experiences with Linux, it's because they are running the wrong distro on the wrong hardware, and they get frustrated.

---

### Post by binbash on 2009-07-09
I would go for another desktop manager like fluxbox.

---

### Post by ibizatunes on 2009-07-09
i run a 800mhz 256m ram on xbuntu no problem, make sure you use ext4 file system when install this will make it a bit quicker still
256 is fine for xbuntu

---

### Post by Znegil on 2009-07-10
I tryed it now, and it works fine.
It is a nice OS and supriced me in a good way.
two problems I have are some letters like a "M" looks like if a printout that got wet, the color is... my english is not good enough to explain it... some look if on a printout the color is not dry and you pull your fingers over it.
I changed the font and now OTHER letters look strange like "4" for example.
Second... how can I make a shortcut for the mail-program on the desktop.
 
I guess everyone uses Windows as a second OS to play some games?

---

