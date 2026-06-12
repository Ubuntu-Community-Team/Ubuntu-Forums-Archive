---
title: "Problem when installing ubuntu 11.04"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by Slasher The Great! on 2011-06-22
[SIZE=2]Does anyone know what this means?

[drm:radeon_ib_schedule] * ERROR * Radeon: Couldn't schedule IB (6)
[drm:radeon_CS_ioctl] * ERROR* Failed to schedule IB
Radeon: Gpu lockup cp stall for more than 10016 msec

If it's a driver issue i've got the linux drivers but i cant boot up so how do i install it?

My graphics card is:
ATi 3850 hd
 ](*,)](*,)](*,)

Thank You
[/SIZE]

---

### Post by dFlyer on 2011-06-22
Why did you start a new thread as your old thread from a few minutes ago lists this problem.

---

### Post by dFlyer on 2011-06-22
Before you installed the OS did you run a live desktop cd to be sure your computer was compatible? Can you get to a terminal by pressing Ctl-alt f2 and run this command:

/usr/lib/nux/unity_support_test -p

all your answers have to be yes to run unity.

Did you check the md5sum of the downloaded iso?

Can you start clasic gnome from the login screen?

Copied from post 4 of your last request. Can you please answer these questions?

Did you run the live cd to make sure your system hardware is supported?

---

### Post by Slasher The Great! on 2011-06-22
i have the cd and it asks me do i want to install it or do i want to try it. if i reinstall it doesnt make a difference and if i click try ubuntu it comes up with the same black screen. it no longer allows me to press ctrl+alt+F2 and the log on screen doesn't appear either.

---

### Post by dFlyer on 2011-06-22
> **Slasher The Great! said:**
> i have the cd and it asks me do i want to install it or do i want to try it. if i reinstall it doesnt make a difference and if i click try ubuntu it comes up with the same black screen. it no longer allows me to press ctrl+alt+F2 and the log on screen doesn't appear either.

You may need to redownload the cd. If you still have the original iso download can you check the md5sum of the iso. The md5sum can be found on the web page you downloaded your iso. If the md5sums match, you may need to reburn the cd at a slower speed. If they don't match you will need to redownload.

Have you done a search on the forum and web about your video card. It may not be compatible, but you should still be able to enter safe mode.

---

### Post by Slasher The Great! on 2011-06-22
[I]**Before you installed the OS did you run a live desktop cd to be sure your computer was compatible?** 
[/I]No ... i was that confident that i would be able to install ubuntu on that computer without having any problems, as i have installed previous versions without any problems

***Did you check the md5sum of the downloaded ISO?***
i don't know how to but heres my md5 number :   MD5:8b1085bed498b82ef1485ef19074c281

***Can you start classic gnome from the login screen?*** 
no because i have set it to auto log in

***Have you done a search on the forum and web about your video card. It  may not be compatible, but you should still be able to enter safe mode.*** 
How do i enter safe mode as i have already downloaded the drivers for the graphics card

---

### Post by dFlyer on 2011-06-22
Lets start with testing the md5sum before proceeding. No need to enter safe mode if the md5sums didn't match.

If you are dual booting you will have to download md5sum.exe, if your using a linux distro md5sum is included.

from a terminal in windows or linux enter the following for the directory you iso is downloaded to:

Linux
md5sum "name of the iso you downloaded without quotes"

Windows
md5sum.exe "name of the iso you downloaded without the quotes"

If they match the md5sum from the website you downloaded your iso from good, if not you will need to redownload.

---

### Post by Slasher The Great! on 2011-06-22
yes they match

---

### Post by dFlyer on 2011-06-22
Great, chances are the cd is good. Now lets boot into recovery mode if we can. To do that you may have to hold down your shift key on a reboot to get into the grub menu. Once there select recovery mode and see if that gets you to a command line or xsafemode option. If you can get this far let me know and we will proceed.

---

### Post by Slasher The Great! on 2011-06-22
ok i held down the shift key and it gave me a bunch of options. i selected recovery mode. the recovery menu came up and i pressed boot with low graphics or something similar. 
it said to select classic gnome on log in i pressed ok and it booted up normally. 
but how do i get it to boot up without doing all of that?
Should i install the drivers?
thank you

---

### Post by dFlyer on 2011-06-22
install your driver

---

