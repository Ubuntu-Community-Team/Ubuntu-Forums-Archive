---
title: "Removing Ubuntu"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by Elvish Legion on 2010-06-24
A friend of mine installed ubuntu on his laptop and doesn't like it, we don't have his recovery discs handy and want to remove ubuntu.  I know normally you'd just use a windows disc to go in and do a fixmbr, but is there a way without that?

---

### Post by Drenriza on 2010-06-24
is he having a ubuntu OS installation on a partition along with a microsoft OS, on another partition?

Since it sounds like, thats what he has done. But you dont say that in your topic.

---

### Post by garvinrick4 on 2010-06-24
Use Ubuntu install disk choosing try ubuntu (live cd)
Restore basic windows boot loader - universe enabled
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```May show error messages about the rest of lilo missing, ignore, we just want MBR

From oldfred on these forums and works nicely.

---

### Post by Rubi1200 on 2010-06-24
> **garvinrick4 said:**
> Use Ubuntu install disk choosing try ubuntu (live cd)
Restore basic windows boot loader - universe enabled
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```May show error messages about the rest of lilo missing, ignore, we just want MBR

From oldfred on these forums and works nicely.

Great tip! 

Does this work irrespective of the installation method? In other words, let's say someone installed Ubuntu choosing the side-by-side option or on a separate partition, would it still work?

---

### Post by garvinrick4 on 2010-06-24
> **Rubi1200 said:**
> Great tip! 

Does this work irrespective of the installation method? In other words, let's say someone installed Ubuntu choosing the side-by-side option or on a separate partition, would it still work?
If you choose Ubuntu in side by side choice at install on last page of install, 8 I believe there will be a advanced tab to put boot into always choose sda. not sda1 or sda5 but always sda
 If you are using a USB drive and it is called sdb then choose sdb in advanced tab. Not sdb1 or sdb5 but sdb
 If the boot gets screwed up using grub2 nowadays it is easy to reinstall grub2 to sda or sdb or where you need with a couple of lines of code. There are lots of good people in these forums who can help with grub problems, just have to ask. Keep your install CD handy now called a Live CD for any purposes to fix your install. grub2 will always boot Windows installs or grub legacy installs. 
    Sometimes Windows users who are just starting out in Linux get there windows boot screwed up a bit and freak out and do not have a recovery CD for fixing windows and just want there Windows boot fixed because they think they are going to lose everything in Windows so this code in the thread is very good for that. I can understand someone that is just trying something out of curiosity losing their boot into Windows and freaking abit though, just part of the process. This paragraph was for new comers and not pointed to anyone specific.

[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by Rubi1200 on 2010-06-25
> **garvinrick4 said:**
> If you choose Ubuntu in side by side choice at install on last page of install, 8 I believe there will be a advanced tab to put boot into always choose sda. not sda1 or sda5 but always sda
 If you are using a USB drive and it is called sdb then choose sdb in advanced tab. Not sdb1 or sdb5 but sdb
 If the boot gets screwed up using grub2 nowadays it is easy to reinstall grub2 to sda or sdb or where you need with a couple of lines of code. There are lots of good people in these forums who can help with grub problems, just have to ask. Keep your install CD handy now called a Live CD for any purposes to fix your install. grub2 will always boot Windows installs or grub legacy installs. 
    Sometimes Windows users who are just starting out in Linux get there windows boot screwed up a bit and freak out and do not have a recovery CD for fixing windows and just want there Windows boot fixed because they think they are going to lose everything in Windows so this code in the thread is very good for that. I can understand someone that is just trying something out of curiosity losing their boot into Windows and freaking abit though, just part of the process. This paragraph was for new comers and not pointed to anyone specific.

[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

Thanks garvinrick4 ):P

I only use Ubuntu, but I have seen so many posts from people asking how to get Windows back that I just wanted some clarification about this method. If you can by any chance remember the thread where oldfred posted this, could you put the link here please?

Thanks again!

---

### Post by garvinrick4 on 2010-06-25
I cannot remember the thread # but this is oldfreds post. I seem to have a habit of putting them into open office format and saving the posts I like. 
--------------------------------------------------------------------------------------------------





You first need to restore the windows boot loader. You can run fixMBR from a windows repair disk or from Ubuntu liveCD.

Restore basic windows boot loader - universe enabled
```
sudo apt-get install lilo
```
```
sudo lilo -M /dev/sda mbr
```
May show error messages about the rest of lilo missing, ignore, we just want MBR

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
The Windows-based Ubuntu Installer (Wubi) allows you to install and uninstall Ubuntu from within Microsoft Windows. It lets a Microsoft Windows user try Ubuntu without risking any data loss due to disk formatting or partitioning.

---

### Post by the8thstar on 2010-06-25
> **garvinrick4 said:**
> Use Ubuntu install disk choosing try ubuntu (live cd)
Restore basic windows boot loader - universe enabled
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```May show error messages about the rest of lilo missing, ignore, we just want MBR

From oldfred on these forums and works nicely.

Garvinrick4 nailed it.

I would add this: after you restore the Windows Bootloader, pop the liveCD in and use "sudo gparted" in the terminal if you want to resize partitions (i.e. destroy the Ubuntu one and enlarge the Windows one).

And that's it. When you restart, Windows will boot (if it was installed on the hdd in the first place of course) and Ubuntu will be gone.

---

### Post by PremiereWebDesign on 2010-06-25
Great Tip.... Not that I need it. If I could get PhotoShop to run in Ubuntu, I would never have to go back and  forth to Windows. But I do see that question asked quite often.

---

### Post by Rubi1200 on 2010-06-25
> **garvinrick4 said:**
> I cannot remember the thread # but this is oldfreds post. I seem to have a habit of putting them into open office format and saving the posts I like.

Thanks! That's a great idea about saving posts by the way.

@ the8thstar; also a nice tip. Thanks

---

