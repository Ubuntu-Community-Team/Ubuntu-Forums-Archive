---
title: "Access existing directory structure NTFS or FAT32"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by harry003 on 2010-04-02
I have installed Lucid on an XP computer running in VirtualBox.

How can I see the entire directory structure (I have multiple hard and optical discs, and also flash and SD drives that come in and out) similar to the way I do in Windows Explorer.

Lots has been written about Mounting but do I have to manually mount each drive (there can easily be a half-dozen, depending on what is plugged in at the time), and do I have to do it every time?

I have heard of Nautilus, where do I find it or do I have to download it separately?

thanks for your help!

---

### Post by arnab_das on 2010-04-02
Nautilus is the file manager of Ubuntu. you dont have to install it. its sort of the windows explorer type thing. you are already using it if ur running ubuntu.

next, if u need to view your windows partitions u would need a windows software. however if u need to view your virtualbox ubuntu's filesystem information, the u can view it through System > Administration > System Monitor and then File Systems tab.

mind u, you cant view your windows partition in virtualbox driven OSes as those OSes are installed under a 'pseudo' partition. hence ur ubuntu will be oblivious of ur windows file system.

hope it helped.

---

### Post by harry003 on 2010-04-02
Thank you for your reply. 

Let me get this straight - say that I have 3 hard drives, 1 flash drive, and 1 SD, card all plugged in.

My VirtualBox is just a small piece of one hard drive, I am serious about migrating off XP but need to test the waters first.

If I want to listen to music on D:, or move some photos from the SD card to my Family Photos directory on C:, or copy some files onto the flash drive to give a friend, I cannot do any of this in Ubuntu and must do it all from within Windows?

I move files around all the time, copy, rename, organize, those are the most fundamental and basic computer tasks to me. 

Am I going to have to make an all-or-nothing decision between Windows and Ubuntu before I can even try out this basic stuff?

---

### Post by 2hot6ft2 on 2010-04-02
> **harry003 said:**
> I have installed Lucid on an XP computer running in VirtualBox.
I have no experience with VirtualBox but on a standard hard drive install you just open any folder and browse to the other partitions that includes windows, SD, USB, or any other drive type. When you open a folder you're in nautilus if running ubuntu.
There are 3 programs for working with NTFS partitions which can be installed either in terminal or by searching for them in synaptic, in aterminal you can install them with
```
sudo apt-get install ntfs-3g ntfs-config ntfsprogs
```
I keep my media music and movies plus file backups on a NTFS partition which I can access from win or ubuntu with no problems.

Once installed ntfs-config will be in
System > Administration > NTFS Configuration Tool
Which only has 4 options to have it set up for internal and external, automatic mounting and read write permissions.

The others you don't need to configure anything

---

### Post by arnab_das on 2010-04-02
> **harry003 said:**
> Thank you for your reply. 

Let me get this straight - say that I have 3 hard drives, 1 flash drive, and 1 SD, card all plugged in.

My VirtualBox is just a small piece of one hard drive, I am serious about migrating off XP but need to test the waters first.

If I want to listen to music on D:, or move some photos from the SD card to my Family Photos directory on C:, or copy some files onto the flash drive to give a friend, I cannot do any of this in Ubuntu and must do it all from within Windows?

I move files around all the time, copy, rename, organize, those are the most fundamental and basic computer tasks to me. 

Am I going to have to make an all-or-nothing decision between Windows and Ubuntu before I can even try out this basic stuff?

yup thats true. however thats only because you are using a virtualbox installation with windows as the 'mother OS'. hence it will enjoy lets say, unhindered access to all ur media. the same logic applies if u had ubuntu as ur 'mother os' and had windows running in virtualbox (however there are ways in which you can make windows in virtualbox access your hard drive which has ubuntu as the main OS). a full fledged wubi installation (i mean an dual booting system with windows and ubuntu) will of course have all features enabled. if u havent tried wubi installation yet, you might want to give it a go as it installs ubuntu like a software which can be removed from ad/remove programs.

one more thing, i think with virtualbox you can access your media (with guest additions, by enabling the particular media -  check the virtualbox menus while your ubuntu is running), but you cannot access windows, not via the vitualbox installation.

---

