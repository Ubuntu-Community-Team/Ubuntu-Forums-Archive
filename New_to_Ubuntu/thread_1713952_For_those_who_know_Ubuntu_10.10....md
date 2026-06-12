---
title: "For those who know Ubuntu 10.10..."
date: 2011-03-24
forum: New to Ubuntu
---

### Post by hh511jas on 2011-03-24
Hello. So I installed Ubuntu 10.10 in my Windows Vista. So far I'm not liking it but that's because I'm not used to it ;), I'm pretty sure I'll get used to it sooner or later :popcorn:. Well you know how you tweak Windows to get the best performance? Well in Ubuntu, is there Services I can disable, start-up programs i can disable, power options, add and remove option, sounds I can disable, etc? 

THIS IS THE QUESTION:

Where and how do I open those applications that allow me to do that :confused:. Like in Windows Vista it has msconfig, services.msc, add/remove, defualt programs, control panel, task manager, etc.

Oh by the way, do I need to install all of those updates in Update Manger?

---

### Post by wilee-nilee on 2011-03-24
First remember that the wubi environment is for testing for your approval for a full partitioned install. It can be transferred to a partition if needed, so customize appropriately with this in mind.

Do not take any grub update/upgrade it will install grub to the mbr when you want the MS bootloader there.

There is a startup applications manager in the menu, but if you notice your ubuntu should be running with about 200-250 memory. The best way to quicken it up would be a partitioned boot.

---

### Post by hh511jas on 2011-03-25
> "First remember that the wubi environment is for testing for your approval for a full partitioned install. It can be transferred to a partition if needed, so customize appropriately with this in mind".

Does that mean I have limited use of Ubuntu and does that mean if I do customize it (like a lot), will it interfere with Windows Vista?

> "Do not take any grub update/upgrade it will install grub to the mbr when you want the MS bootloader there".

What does that mean and can I get an example?

Thanks for the advice...

---

### Post by wilee-nilee on 2011-03-25
> **hh511jas said:**
> [FONT="Tahoma"][SIZE="2"]

Does that mean I have limited use of Ubuntu and does that mean if I do customize it (like a lot), will it interfere with Windows Vista?



What does that mean and can I get an example?

Thanks for the advice...[/SIZE][/FONT]

A wubi is a pseudo virtual, a file inside of windows, it is not set up as a regular install, and is subject to any errors in Vista. Length of use doesn't matter, customize it all you want, just recognize the tenuous state that that type of install is in.

Here is the wubi megathread, that has two common problems, and will give you an idea of grub overwriting the mbr. 
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Here is the wubi wiki.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Rubi1200 on 2011-03-25
I think this is a good place to start looking for answers to some of your questions:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick](http://ubuntuguide.org/wiki/Ubuntu:Maverick)

> [FONT=Tahoma][SIZE=2]Oh by the way, do I need to install all of those updates in Update Manger?[/SIZE][/FONT]
Yes, but only after locking the grub packages (see main post of the first link wilee-nilee linked to).

You should also keep a backup copy of the root.disk somewhere like a USB stick.

Also, make sure you have an Ubuntu CD available if you ever need to troubleshoot and fix something.

Finally, remember that because Wubi uses a virtual diisk inside Windows it is vulnerable to some of the problems often encountered in Windows e.g. defragmentation etc.

---

### Post by beew on 2011-03-25
I suggest a real dual boot or installing Ubuntu in an external hard drive if you want to try Ubuntu for real. WUBI doesn't give you the true picture of what Ubuntu is capable of, it is a Windows program that works out of a folder basically.

---

### Post by 29732 on 2011-03-25
You should read this -- [http://ubuntu-manual.org/](http://ubuntu-manual.org/)
It tells all of the basics of ubuntu

---

### Post by steveneddy on 2011-03-25
> **beew said:**
> I suggest a real dual boot or installing Ubuntu in an external hard drive if you want to try Ubuntu for real. WUBI doesn't give you the true picture of what Ubuntu is capable of, it is a Windows program that works out of a folder basically.

Agreed.

Wubi is for a short term trial time of Ubuntu anyway.

Do not waste your time customizing Ubuntu while running it in Wubi.

Either partition the drive and install Ubuntu in it's own partition

-OR-

install VirtualBox on Windows and install Ubuntu inside of VB - it's easier to run that way and you can learn much about both OS's until you decide to ditch Windows altogether and give Ubuntu the entire drive.

I use Windows 7 in VirtualBox installed on Ubuntu and it works great for me.

---

### Post by goldblattster on 2011-03-26
> **hh511jas said:**
> [FONT="Tahoma"][SIZE="2"]
What does that mean and can I get an example?

Thanks for the advice...[/SIZE][/FONT]

What he means when he talks about the MBR...

The MBR is a a bit like a portion of space on your hard drive that has a bootloader. A boot loader is basically a small file within windows that lets you load/boot into your OS. Wubi is based on the Windows Bootloader (that's the screen where you can choose to boot into either Ubuntu or Windows). Wubi is a sort of pseudo-windows. If you overwrite the Windows Bootloader with grub you might not get the "listings" (the "database" of things the bootloader can boot into). grub is the bootloader that ubuntu mainly uses (except for wubi). Basically, if you install grub you may lose windows, although you can recover your windows bootloader by inserting your Windows disk in and running "/fixmbr" in the recovery console it can be a pain.

---

### Post by hh511jas on 2011-03-27
Got it, I understand now. I'll see what I can do. Thank you very much ):P. Peace.

---

### Post by aaaaalex on 2011-03-27
Going back to your originial post...

If you are looking for a program to 'Tweak' you ubuntu, you may want to check out UbuntuTweak [Here is how to install it.]("http://www.ubuntugeek.com/ubuntu-tweak-0-5-7-released-with-ubuntu-10-10-maverick-ppa-updates.html")

In case you want the Desktop Cube and heavily work on how things look and behave on the surface, you may want to install the CCSM, wich will live under System -> Preferences

```
sudo apt-get install compizconfig-settings-manager
```

Regarding the WUBI Situation: I agree with what has been said regarding that. You should consider making some way on your HDD for a proper install. Especially if you are looking into making your Machine run as fast as possible. WUBI makes Ubuntu live inside a giant File on your Windows partition - that causes some overhead naturally.

---

### Post by madjr on 2011-03-27
to learn some cool stuff you can do with ubuntu and what's coming , i suggest checking these sites:

[http://www.omgubuntu.co.uk/](http://www.omgubuntu.co.uk/)

[http://www.webupd8.org/](http://www.webupd8.org/)

---

