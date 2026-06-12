---
title: "system wont find OS on start up"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by gidrdunv11 on 2008-12-16
I went through a step by step to do a dual boot with ubuntu installed first but the WindowsXP install CD didn't work. Computer would only recognize windows in the partition I created and not the original partition with Ubuntu. I deleted the partition with windows on it and still won't find original operating system.

---

### Post by Titan8990 on 2008-12-16
A Windows disc will never find a Linux partition.

---

### Post by OutOfReach on 2008-12-16
Yeah Windows only recognizes NTFS and FAT partitions. It shows any other kind of partition as unknown.

---

### Post by rzrgenesys187 on 2008-12-16
I might not have read the problem correctly, but if you've installed windows it will overwrite your grub.  To reinstall grub (assuming ubuntu has already installed) you can use this howto.  It has worked wonders for me in the past [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by gidrdunv11 on 2008-12-16
The disk didn't work so I just gave up on it. Not using the disk now only want my computer to startup using the original operating system

---

### Post by gidrdunv11 on 2008-12-16
Yes the grub. when I type in grub "find /boot/grub/stagel/", I get "file not found". Don't know what to try next!?

---

### Post by bumanie on 2008-12-16
From a live ubuntu cd > sudo fdisk -lu in terminal - post the output to the forum

---

### Post by maddog46113 on 2008-12-16
> 
This option will use the Desktop/Live CD to install Grub into your MBR (Master Boot Record). This option will overwrite your Windows Boot Loader It is OK to do this, in fact that is the goal of this how to (in order to boot Ubuntu) B)

1. Boot the Desktop/Live CD.

2. Open a terminal (Applications -> Accessories -> Terminal)

3. Start grub as root with the following command :

    *

      sudo grub

4. You will get a grub prompt (see below) which we will use to find the root partition and install grub to the MBR (hd0,0)

    *

               [ Minimal BASH-like line editing is supported.   For
               the   first   word,  TAB  lists  possible  command
               completions.  Anywhere else TAB lists the possible
               completions of a device/filename. ]

      grub>

      Type the following and press enter:

      find /boot/grub/stage1

      If you get "Error 15: File not found", try the following:

      find /grub/stage1

      Using this information, set the root device (fill in X,Y with whatever the find command returned):

      grub> root (hdX,Y)

      Install Grub:

      grub> setup (hd0)

      Exit Grub:

      grub> quit

5. Reboot (to hard drive). Grub should be installed and both Ubuntu and Windows should have been automatically detected.

6. If, after installing grub, Windows will not boot you may need to edit /boot/grub/menu.lst (That is a small "L" and not the number 1 in menu.lst)

    * Open a terminal and enter :

       gksu gedit /boot/grub/menu.lst

      Or, in Kubuntu:

       kdesu kate /boot/grub/menu.lst

      Your Windows stanza should look something like this :

       title Windows XP/Vista # You can use any title you wish, this will appear on your grub boot menu
       rootnoverify (hd0,0) #(hd0,0) will be most common, you may need to adjust accordingly
       makeactive
       chainloader +1

      Note: Put your Windows stanza before or after AUTOMAGIC KERNEL LIST in the menu.lst 

source: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by 3rdalbum on 2008-12-16
> **gidrdunv11 said:**
> Yes the grub. when I type in grub "find /boot/grub/stagel/", I get "file not found". Don't know what to try next!?

It's "stage1" (the number 1), not "stagel".

---

### Post by JUDOHAWK on 2008-12-16
I had the same problem, I tried to install windows AFTER I had ubuntu first. Well the setup disc would not recognize any partition even after partitioning in NTFS. Well I used the recovery discs and got Vista back on, but then I installed ubuntu after I had vista.  That seemed to be the best way for me to dual boot. That way you don't have to go restoring the GRUB.

---

### Post by waspbr on 2008-12-16
the easiest way to do it is to install windows and then install ubuntu. What I generally do is just to use the live CD to partition the HDD as I want (with gparted , system > Administration > Partition editor ) Then I create 1 ntfs partition for windows and leave the rest unpartitioned. then I would reboot install windows into the ntfs, and after that I would install ubuntu.

---

### Post by gidrdunv11 on 2008-12-17
here is what came back



Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd4e926e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    75152069    37576003+  83  Linux
/dev/sda3        75152070    78124094     1486012+   5  Extended
/dev/sda5        75152133    78124094     1485981   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

