---
title: "best way of installing xp while still having ubuntu?"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by ChubbySauce on 2009-12-20
I want xp cause a lot of programs I use with wine still aren't compatible, lot of game programs.

anywho I would still like ubuntu as my main and first OS to boot I have a xp installation disk?

Anyone have any experience or know how I would do this?

---

### Post by spiky001 on 2009-12-20
Hi i have dual booted when i started the forum all told me to load xp 1st then ubuntu afterwards never had a problem

---

### Post by bodhi.zazen on 2009-12-20
You can install either OS in any order.

Prep space (partitions) first =)

If you install Windows second you will need to restore grub :

[Recovering Ubuntu after installing Windows - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by nch0930 on 2009-12-20
I'm an absolute beginner too, but I believe I can help you with this.

Dual Boot is OK, but only if you have a device that doesn't work with Ubuntu (for me, my webcam), so I log on XP only when I need to video chat.

For everything else, is a better idea to use VirtualBox OSE (it's on Ubuntu software center).
You basically run XP inside Ubuntu, it works great! You no longer need to reboot and change OS just to run that program that only works under Windows.

Give it a try, it's great.

Good luck.

---

### Post by uberdonkey5 on 2009-12-20
I've reinstalled ubuntu several times with dual boot and also tried virtualisation (virtual box).

People say virtualisation of xp is faster than running it normally, but I doubt if it makes much difference. I also think there are several benefits of dual booting over virtualisation: i. booting one of two operating systems means that if you have a problem in one you can use the other ii. virtualisation sometimes has problems (I had problem with the mouse and screen size previously).

So.. I recommend dual boot. If you don't want to mess with partitioning yourself (which can be a pain).. install xp first (and choose to format HD when you install, so that everything is clean). Then install ubuntu. Don't forget, ubuntu can manipulate files you use in windows, but windows won't recognise the ubuntu drive space, so you need to base your estimate of HD partitioning for ubuntu (very simple when you install ubuntu) on how much space you think you'll require in windows.

Once ubuntu is installed the grub (the boot loader that lets you choose ubuntu or windows at the start) will default to start ubuntu. However, if you rarely use windows, you may want to reduce the time delay in the grub menu to e.g. 1 or 2 seconds so that ubuntu starts up pretty fast.

to do this, you need to edit a file which determines the boot up list. This is different for ubuntu 9.10 to previous versions...see:

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

to edit the grub menu, edit this file as follows:

sudo gedit /etc/default/grub

in this, where it says 'timeout' change the number to the number of seconds you want it to delay before automatically starting the first choice. Of course, in this file you can also change the boot menu to start windows by default automatically, or get rid of some of the options.

then save and type:

sudo update-grub


hope this is useful!!

---

### Post by oldfred on 2009-12-20
This site shows the process:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

It still has Ubuntu 8.04 but the process is the same. If you have the newest 9.10 with grub2 the reinstall process for grub2 is a lot different so do not mix them up.

Herman also has a variety of dual boots installs, may be too much info:):
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by ChubbySauce on 2009-12-20
wow ^^;

those instructions [[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054") gave me look awfully complicated I think I might just use virtual box

xp sorry Im new to ubuntu and dont want to mess up my os

---

