---
title: "Two hard disks, two OS"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by emiliano67 on 2009-08-31
I've read many posts about this...and still couldn't figure it out..
I have a hard disk with XP and Ubuntu(WuBi) installed. I get the normal choice when I switch the computer on, Windows or Ubuntu, choose what I need, no problem.
I have an older hard disk (40GB) that so far I have used as storage. The first one is the master and the second the slave. In Windows I see all the partitions, no problem. In Ubuntu I see the windows part of it (in the /host folder, all correct) in the same hard disk Ubuntu is installed on and can access it, no problem, but cannot find the other hard drive, cannot access it. That's because of the Wubi installation? 
What I want to do is erase all the data on the old hard disk and install Ubuntu on it. Then uninstall Ubuntu that is now running alongside windows so that I would have an hard disk all windows and one all Ubuntu(and speed up the process of getting rid of windows completely). But, from windows, where I can access the hard disk, I can only format it for NFTS. And since I cannot access it from Ubuntu...what can I do? I have the CD but I cannot figure out how to get it to install Ubuntu on the older hard drive, the slave used as storage. Maybe because it's a slave? Cables are different, wouldn't know how to switch from master to slave.
Thanks

---

### Post by Liolikas on 2009-08-31
With one HHD and partitions things are more simple. 

Ubuntu can use ntfs too, but ntfs-3g drivers needed (usa package manager for it). If you do not plan large files like few Gb you can use fat32 too Windows can use it and Ubuntu.
Basically I think you have to install Ubuntu into master and windows slave and Grub will be still able to boot things from slave if it is in master itself. But my last and only 2 hdd dual boot setup was Windows and Linux root in master and data fat32 and /home in slave.

Here old thread about same things. But do not go into deep too much Ubuntu installation procedure changed totally if compared with 2006.
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)
Just those /boot/grub/menu.lst examples and tricks are good and interesting in case boot fails to windows or ubuntu.

---

### Post by Elfy on 2009-08-31
> ...erase all the data on the old hard disk and install Ubuntu on it. Then uninstall Ubuntu...
I would be inclined to do it the other way - but obviously the choice is yours :)


Remove ubuntu from windows with it's add/remove. Check that windows still boots.

Boot with the livecd and install to the second hdd - it will be called sdb(x). Depending on how many partitions are on the second hdd it could just be sdb1.

You should be able to see the second drive form the partitioner, if you are not sure from a terminal on the livecd run this and paste the output.

```
sudo fdisk -l
```

If you cannot see the second drive in the partition part of the installer - post a screenshot.

---

### Post by emiliano67 on 2009-08-31
Thanks for the usual fast responses. In the meanwhile I also thought that I can transfer the Wubi installation into its own partition (LVM) and then forget about the older hard disk. What forestpixie says sounds the best way but...I would avoid to do all the reinstalling updates and packages...I backed up my current system (using tar as per thread [http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)) but, when I try to open the file I get, it's says, at a certain point in the process of opening it, that there are errors and it's impossible to open the archive. I tried several times, always with the same result. Following forestpixie sound advice I would loose everything and would have to reinstall it all. Any suggestions on backup, then?...forestpixie...?

---

### Post by Elfy on 2009-08-31
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

I have used the simple backup suite in the past, that said all I usually need to backup prior to a reinstall is a few things in my /home as I keep my data elsewhere so it all fit's on a small USB stick.

What you could do is do the new install on the second harddrive, not delete the wubi one. Once you've installed you should be able to access the wubi files from the new install - [https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?](https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?)

But I also tend to forget the LVM option as well so that might be worth doing instead ;)

---

### Post by emiliano67 on 2009-08-31
Thanks, forestpixie. But that's my original problem: I don't know how to install on the older hard disk. If I put the Ubuntu CD into the computer, running Windows, it says that if I want to do Demo and Full Installation I have to reboot the computer. I restart, it goes to the choice of OS screen (GRUB) and if I choose Windows, it opens Windows normally, no CD in action..cannot install.

---

### Post by Elfy on 2009-08-31
aaahh - is the PC set to boot from CD first - it has to - then you will boot with the CD and it will not boot to windows first.

Change the boot order in BIOS or if it's fairly new you might have a choice - check the screen as it boots

---

### Post by halitech on 2009-08-31
you need to go into the BIOS and set the computer to boot from the cd first

---

### Post by emiliano67 on 2009-08-31
Thanks guys, I know how to do that. I'm on it, will let you know what happens...

---

### Post by Elfy on 2009-08-31
Don't install to the wrong drive :)

---

### Post by emiliano67 on 2009-08-31
Not good. It goes to the BusyBox...I think if Ubuntu is installed with Wubi the CD doesn't work. Is it possible? I've found tons of threads about getting into the BusyBox but no solution.

---

### Post by halitech on 2009-08-31
could be a video card issue, what video card do you have? (general system specs might help as well)

---

### Post by emiliano67 on 2009-08-31
Intel Core 2 Duo CPU E7400 @ 2.80 GHz, VGA is Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10), but I have had no problem at all installing Ubuntu with Wubi and it still works perfectly, all of it, Ubuntu and Windows.

---

### Post by halitech on 2009-08-31
maybe try the alt install cd, nothing against the devs but the live cd is not all its cracked up to be in my experience.

---

### Post by emiliano67 on 2009-09-01
Ok, I uninstalled Wubi from Windows. Defragmented the hard drive. Then installed Ubuntu from the CD following the procedure: I allocated 100 GB of the hard drive (it's 250 GB) to Ubuntu and went ahead. All good. 

I tried the PartitionManager before doing this but the downloads must be corrupted because I had it in the boot choice screen (you know, choose the OS: Ubuntu, XP, partitionmanager) as it was supposed to be but when chosen it would start and then stop and give an *error 23 : Error while parsing number*. I tried to reinstall the package and looked at the terminal, following the process. It gave a _Syntax error_ at the end. So, my personal newbie advice is this:

[LIST=1]
[*]forget about the CD when Wubi is installed
[*]uninstall Wubi before you install Ubuntu on a real partition
[*]before you uninstall Wubi, create a file that you can use to reinstall all the packages you already have :dpkg --get-selections > selections.dpkg
[*]save it on an external hard drive
[*]after reinstalling the system, plug in your external hard drive, open Synaptic, go file > read markings, select that file that was generated (selections.dpkg), press apply, and it'll reinstall all the software you have on your current system(useful tip, found at [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591) under Alternative Instructions)
[/LIST]
Thanks to everybody for your help.

---

