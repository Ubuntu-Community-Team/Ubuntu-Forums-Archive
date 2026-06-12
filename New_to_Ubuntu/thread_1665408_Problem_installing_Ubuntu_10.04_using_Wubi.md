---
title: "Problem installing Ubuntu 10.04 using Wubi"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by Morkid on 2011-01-12
Hello,

I'm an absolute first timer using Ubuntu, I'm using psychocats guide to install Ubuntu using Wubi. I ran wubi.exe, but when rebooting to ubuntu it appears to start installing, but then I just see what appears to be a lot of lines of prompts or script messages or something, looks kind of like:

[ 0.869896][fffffffff02912] &child-precess 0x0

something like that, I don't remember exactly and I couldn't copy it. I noticed that only the power indicator light was on, so I figured it wasn't doing anything, let alone installing. 

I just downloaded the iso and wubi, am I missing something? I have no idea what to do.

I'm using a Toshiba satellite running Windows 7 Home Premium 64bit, Intel core i3 CPU 4Gb RAM.

thanks

---

### Post by zeroseven0183 on 2011-01-12
Did the process stopped? I mean did the messages froze on a particular line? If yes, which one?

---

### Post by Nickjpost on 2011-01-12
In Windows 7, there is a nifty image burner, try to burn the .iso image to disk (Ubuntu is small enough to fit onto a CD, I think it's only like 695 MB or something like that).
After you have the live image to disk, restart your computer and either config bios or go to boot selection (it varies, but usually you press F12 to select a boot device) and choose CD/DVD. You can also just load the CD in Windows and run the CD. Ubuntu should give you the option to try the install along side Windows. 
 
Hope this helps you out!

---

### Post by Morkid on 2011-01-12
The last few lines I get are:

[0.867173][<ffffffff8184d7e5>]kernel_init0x102/0x156
[0.867235][<ffffffff810141ea>]child_init0xa/0x20
[0.867296][<ffffffff8184d6e4>]? kernel_init+0x0/0x156
[0.867358][<ffffffff810141e0>]? child_init+0x0/0x20

If I boot it from a CD, will I still be able to install it with Wubi? I don't want to start messing with my Windows installation, partitioning etc.

EDIT: I tried booting from a DVD, but I got almost the same thing: a flashing cursor and only the Power indicator lights are on, so I think I probably need download the iso again.

---

### Post by bcbc on 2011-01-12
Toshiba's seem to have issues booting ubuntu. What's the make/model? Try searching with that on google (site:ubuntuforums.org toshiba xxxx) and see what others have done.

Also make sure your bios is up to date. 

Heads up: if you get it going with Wubi, you want to avoid updating grub (packages grub-pc and grub-common). You can lock these packages or just uncheck them from Update Manager. See the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") for details.

---

