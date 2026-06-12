---
title: "Backing up Wubi install of Ubuntu 10.04.1"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by tonycm1 on 2011-02-12
I have a laptop that work provided me that has XP installed on it. I've installed Ubuntu 10.04.1 via Wubi a few months ago and have been using it whenever I'm not at work and love it.

Unfortunately, my work is re-imaging all laptops and i'm worried that I'll lose my ubuntu setup. 

I know that the WUBI guide says:
> Can I back up the installation files?

Yes; just copy C:\ubuntu\disks\root.disk somewhere else (in 7.04 the relevant files are called C:\wubi\disks\*.virtual.disk). Old installation files can be mounted within Ubuntu and any relevant data can be copied over the new installation.

But does this only apply for backing up your image on a current WUBI install or would I be able to backk up the wubi folder and then when I receive the laptop back from work, re-install wubi and override the files with my backed up version?

Thanks for the help... love the forums here! :)

---

### Post by Frogs Hair on 2011-02-12
Reimaging by some definitions or a method of returning the hard-drive to its original state  . If this what is being done to the work computer you will lose everything. I have no way of knowing what your companies procedure  is.

Backing up your home folder data may be a good option . It is always a good idea to check software policies at work before installing any software especially on company property.

---

### Post by tonycm1 on 2011-02-12
So if I backup the C:\ubuntu\disks\root.disk folder, would I then be able (once I receive the new laptop with XP) to install WUBI (standard installation) and then copy my backup C:\ubuntu\disks\root.disk folder to the new directory? :confused:

---

### Post by Frogs Hair on 2011-02-12
I'm suggesting storing your data on a removable device or cloud storage  if you have that option and adding it to a new Wubi installation.

---

### Post by tonycm1 on 2011-02-12
I already have a system of backing up my /home data to the cloud, however, i'm more concerned about the tweaks that I've added to Ubuntu that were extremely time consuming and much of a learning experience. That's the reason I want to backup my c:\ubuntu folder to a Removable HD with the hopes of restoring that same image once I get my laptop back.

---

### Post by Frogs Hair on 2011-02-12
I was thinking terms of Ubuntu being removed from the computer . I'm assuming  they will reinstall XP and work related software , but the files in Windows that allow Ubuntu to boot will most likely be removed.

Here is an option you can look at as far as a complete image backup goes. 
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by bapoumba on 2011-02-12
To echo one of the comments here, does your company allow you to change their setup and install other softwares ?

---

### Post by tonycm1 on 2011-02-12
> **bapoumba said:**
> To echo one of the comments here, does your company allow you to change their setup and install other softwares ?

Officially, they don't allow non-standard software on the laptop.

Unofficially, the IT group turn a blind eye to most non-standard software on the computers.

---

### Post by tonycm1 on 2011-02-12
> **Frogs Hair said:**
> I was thinking terms of Ubuntu being removed from the computer . I'm assuming  they will reinstall XP and work related software , but the files in Windows that allow Ubuntu to boot will most likely be removed.

Here is an option you can look at as far as a complete image backup goes. 
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

Looks like a good tool... but my image is about 15gigs (after removing music, movies etc..) so this solution won't work :(

I find it hard to believe that there isn't a way to revert back to a previous WUBI image :(

---

### Post by bapoumba on 2011-02-12
> **tonycm1 said:**
> Officially, they don't allow non-standard software on the laptop.

Unofficially, the IT group turn a blind eye to most non-standard software on the computers.

Okay thanks :)

---

### Post by bapoumba on 2011-02-12
[http://ozansafi.wordpress.com/2010/04/11/how-to-backuprestore-a-wubi-installation/](http://ozansafi.wordpress.com/2010/04/11/how-to-backuprestore-a-wubi-installation/)

I have looked around. This is an offsite link and I have not verified it works (not using wubi).

---

### Post by bcbc on 2011-02-12
> **tonycm1 said:**
> Looks like a good tool... but my image is about 15gigs (after removing music, movies etc..) so this solution won't work :(

I find it hard to believe that there isn't a way to revert back to a previous WUBI image :(

You can do it.

In the \ubuntu\disks folder are the .disk files. Copy these on to an external drive.
Then on the new computer, install the same release of Ubuntu. Before the first reboot (still in windows), copy those .disk files back into the \ubuntu\disks folder.

Then when Ubuntu boots, you'll see your familiar Grub menu appear. But don't hit enter - it won't boot. THe reason is that the grub menu (it's from your original root.disk) is referencing the UUID from your old partition (gone) also the physical partition (e.g /dev/sda2 may have changed as well depending on the new setup).

1. You will have to identify the new partition.
2. Then override the first menu entry in Grub as follows:
hit 'e' to edit
delete the line starting "search" (that sets root to the old uuid)
change (hdX,Y) to the correct partition
change /dev/sdaY to the correct partition
Hit CTRL+X to boot
Login, drop to a terminal and run "sudo update-grub" to fix the grub menu.
Done.

This is how to identify your partition from a grub command line - hit 'c' when you see the grub menu.
search -s -f -n /ubuntu/disks/root.disk
echo $root

Based on what the output is find the partition
(hd0,1) = /dev/sda1
(hd0,2) = /dev/sda2
(hd0,5) = /dev/sda5
(hd1,1) = /dev/sdb1
Use these values to substitute when you edit the grub menu entry above.

Simple... (not)

(Hit ESC to go back to the grub menu from a command prompt - or "reboot" if you get stuck)

[https://wiki.ubuntu.com/WubiGuide#Warning](https://wiki.ubuntu.com/WubiGuide#Warning)

PS on 10.10 grub refers to partitions as (hd0,msdos1). If that's the case just do the same e.g. (hd0,5) = (hd0,msdos5)

---

