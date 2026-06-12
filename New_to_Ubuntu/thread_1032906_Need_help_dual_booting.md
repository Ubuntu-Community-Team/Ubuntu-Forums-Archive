---
title: "Need help dual booting"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by Dravenm4 on 2009-01-06
Hello all,
I have a question I have installed ubuntu 8.04 already and i want to dual boot it with backtrack 3 from a usb live stick. How should i start this, what ive read is to install bt3 then reinstall grub or something like that but when i install ubuntu it partitioned all of my hard drive for ubuntu. advice please? I'm installing on a toshiba satellite 2gigs of mem. 80gig HDD.

---

### Post by Dravenm4 on 2009-01-06
Also I have gparted but it will not let me resize?I dont know

---

### Post by beattyml1 on 2009-01-06
In order to repartition you need to have the drive that you are partitioning unmounted, the easiest way to do this is boot into an ubuntu live cd and use gparted from there, this will then allow you to operate on your hard drive with it unmounted

as to installing grub I don't know, as I've never done that

---

### Post by Dravenm4 on 2009-01-06
thanks for that bit of advice. 

any idea as to how to dual boot another linux os with ubuntu or how i should go about it?

---

### Post by 2hot6ft2 on 2009-01-06
> **Dravenm4 said:**
> i want to dual boot it with backtrack 3 from a usb live stick.
What you want is called a usb live install with persistent changes and is covered in detail in the forum for bt3. I suggest a search here.
[http://forums.remote-exploit.org/index.php](http://forums.remote-exploit.org/index.php)

Here you go. [http://forums.remote-exploit.org/showthread.php?t=18671](http://forums.remote-exploit.org/showthread.php?t=18671)

That way when you want to run bt3 you put the usb stick in and boot up to it. When not using bt3 you boot up without the usb stick plugged in.

That's how I do it as well and I put bt3 on a SD card so it doesn't stick out like a usb stick and I still have use of all my usb ports.

---

### Post by Dravenm4 on 2009-01-06
thank you 2hot6ft2, But I have the usb live distro and that is what i am going to use to install to my HDD for dual boot, I tried the usb version for a while but to many problems stemming from the fact it is a usb stick and didnt initialize the wireless card most of the time. so thanks anyway I just am new to linux and never dual booted before.... so i dont know where to start.

---

### Post by 2hot6ft2 on 2009-01-06
The how to there for installing to a usb can be used for a hard disk install with a few changes. they have plenty of how to's including dual booting with ubuntu and even triple booting bt3 with ubuntu and windows.

Personally I'm waiting for bt4 to come out which from reading it sounds like it may come with an installer and use KDE. It should be out pretty soon and I'm anxious to see the changes.

BT3beta came with an installer but uses LILO, you can still get it from their download pages using the older versions link at the bottom or go here for a how to that has the missing installer.

[http://kin.calvin.free.fr/blog/?p=16#comment-1821](http://kin.calvin.free.fr/blog/?p=16#comment-1821)

You have to put the entry for bt3 into the menu.lst file by hand.

---

### Post by Miljet on 2009-01-06
First of all, I know nothing about bt3. But I have an old computer that I use to experiment with different versions. Whenever I install any new distro, I install it WITHOUT any boot loader. This is found in advanced options during install. Then I boot into Ubuntu  and edit the /boot/grub/menu.lst file to add entries for the new distro. That eliminated a lot of confusion for me.

The best guide for working with GRUB that I have found is here:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

