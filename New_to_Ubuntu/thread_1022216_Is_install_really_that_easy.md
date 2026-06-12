---
title: "Is install really that easy?"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by ZenBuddhistDog on 2008-12-26
Hey,
I'm currently a Vista User, but i want to dual boot Ubuntu.
I've read a few tutorials on how to get it working, and it seems really easy.
I've heard horrible things about trying to get 2 OSs running on one machine, and I dont want to horribly screw up my computer.
here's the tutorial in question
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1")

thanks for the help.

-ZBD

---

### Post by Dedoimedo on 2008-12-26
Setting up dual boot is easy. But ...
You should know what you're doing and backup your data.
You should understand Linux drive/partition notations.
You should know where your Windows resides...

I would recommended against any automatic choices of partitions or space. I'd go for manual selection ...

Maybe this will help you, too:
[http://www.dedoimedo.com/computers/dual_boot.html](http://www.dedoimedo.com/computers/dual_boot.html)

Dedoimedo

---

### Post by HotShotDJ on 2008-12-26
> **Dedoimedo said:**
> I would recommended against any automatic choices of partitions or space. I'd go for manual selection+1  -- I couldn't agree more.  And if you don't fully understand what you are doing, then browse the Ubuntu documentation ( [https://help.ubuntu.com/community](https://help.ubuntu.com/community) ), Google, and ask here.  Learn all you can and then enjoy your new operating system and software.

---

### Post by steveneddy on 2008-12-26
I personally set up my partitions first. You can use a gparted LiveCD to accomplish that goal.

---

### Post by spiderbatdad on 2008-12-26
Not all hardware is linux compatible. Linux comes with no warranty. You assume all responsibility for the installation of linux onto your computer. Whether microsoft will warranty your computer after you partition and install a secondary OS, I do not know.
I guess I would recommend finding a second computer you are willing to run Ubuntu on, without the fear of damaging your existing system. This is not to imply there is any intrinsic risk of damage, but if you are concerned, you must protect yourself.

---

### Post by nlz on 2008-12-26
I did 50+ installs and never lost any data BUT you should ALWAYS backup your data. And.. yeah.. it's really easy. Especially if you print out a guide and have a spare PC with internet connection if you have any question..

---

### Post by ugm6hr on 2008-12-26
> **ZenBuddhistDog said:**
> I've heard horrible things about trying to get 2 OSs running on one machine, and I dont want to horribly screw up my computer.

Installing an OS (any OS) is not straightforward for anyone who doesn't know what they're doing.  But it's pretty easy with Ubuntu.

Installing a dual-boot system is a different story.  If you don't know what you're doing, it is entirely possible to wipe your HD etc.

So - if you want to pursue this - consider doing the following first:
1. Do lots of reading first.
2. Find a friend who knows what they're doing
3. Backup everything of any value (including other OS)

---

### Post by kansasnoob on 2008-12-26
> **ZenBuddhistDog said:**
> Hey,
I'm currently a Vista User, but i want to dual boot Ubuntu.
I've read a few tutorials on how to get it working, and it seems really easy.
I've heard horrible things about trying to get 2 OSs running on one machine, and I dont want to horribly screw up my computer.
here's the tutorial in question
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1")

thanks for the help.

-ZBD

That's a very good tutorial. Yes, it's that simple!

Resize Vista using only Vista's own tools, just leave the free space unallocated, then be sure to choose "Guided-use largest continuous free space".

Of course before installing try running the Live CD (just choose, "Try Ubuntu without any changes to your computer") and see if your hardware seems to agree with Ubuntu. That is, how does it look, how does it sound, can you connect to the internet?

Just keep it simple!

---

### Post by ajgreeny on 2008-12-26
The best guides to installing ubuntu are here
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
Look at the various pages indexed on the left of this page and it will tell you just about anything you need, or want to know about dual booting, or anything else to do with installing etc etc.

---

### Post by nhasian on 2008-12-26
have you considered using wubi?

[http://wubi-installer.org/](http://wubi-installer.org/)

Wubi is an officially supported Ubuntu installer for Windows users that can bring you to the Linux world with a single click. Wubi allows you to install and uninstall Ubuntu as any other Windows application, in a simple and safe way. Are you curious about Linux and Ubuntu? Trying them out has never been easier!

[LIST]
[*]Wubi is Simple -  No need to burn a CD. Just run the installer, enter a password for the new account, and click "Install", go grab a coffee, and when you are back, Ubuntu will be ready for you.
[*]Wubi is Safe - You keep Windows as it is, Wubi only adds an extra option to boot into Ubuntu. Wubi does not require you to modify the partitions of your PC, or to use a different bootloader, and does not install special drivers. It works just like any other application. Wubi is spyware and malware free, and being open source, anyone can verify that.
[*]Wubi is Discrete - Wubi keeps most of the files in one folder, and if you do not like it, you can simply uninstall it as any other application.
[/LIST]

[IMG]http://wubi-installer.org/images/wubi-123_small.png[/IMG]

---

