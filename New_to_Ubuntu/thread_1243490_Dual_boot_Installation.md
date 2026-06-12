---
title: "Dual boot Installation"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by masthijohna on 2009-08-18
Hi,
     I'm new to Ubuntu.I tried to intall ubuntu 9.04 dual boot with Xp but at the end of the installation , in the import list there wasn't any versions(XP) to import.But when i installed ubuntu 9.04 in another machine dual boot with XP , XP was in the import list.If i ignore it and go forward will XP be there without any errors? How can install Dual boot correctly?

---

### Post by jacklinux on 2009-08-18
Do you mean the option to boot XP isn't showing on the bootup?

---

### Post by killersla on 2009-08-18
i have used geparted for all my formatting and partioning.  I think the best thing to do would be to download geparted make a bootbale cd and create a new partition on your drive.  Then from windows install it onto the new drive restart and you will be givin the option of xp or ubuntu.
 
Well that worked well for me anyway.
 
regards
 
Killersla

---

### Post by jacklinux on 2009-08-18
> **killersla said:**
> i have used geparted for all my formatting and partioning.  I think the best thing to do would be to download geparted make a bootbale cd and create a new partition on your drive.  Then from windows install it onto the new drive restart and you will be givin the option of xp or ubuntu.
 
Well that worked well for me anyway.
 
regards
 
Killersla
Or you could use Wubi installer in windows.

---

### Post by anung524 on 2009-08-18
are you sure you really have 2 partitions before installing ubuntu next to the xp?

---

### Post by killersla on 2009-08-18
> **anung524 said:**
> are you sure you really have 2 partitions before installing ubuntu next to the xp?
 
 
If you want a dual boot system then i believe the answer is yes.  You need 2 partitions with the 2 different os so your pc will give you the option to boot from either xp or ubuntu.

---

### Post by presence1960 on 2009-08-18
I think you guys are way off base here, the OP is saying during the install process he is not given an option to import any accounts (like from XP or Mozilla).

Your XP install will be safe if you proceed. The option to import does not affect the other partitions, if there is an option such as a mozilla account it will import that into the new Ubuntu installation without affecting the existing installation from which it is taken. if you import nothing your Ubuntu and XP install will be fine also.

---

### Post by masthijohna on 2009-08-18
> **presence1960 said:**
> I think you guys are way off base here, the OP is saying during the install process he is not given an option to import any accounts (like from XP or Mozilla).

Your XP install will be safe if you proceed. The option to import does not affect the other partitions, if there is an option such as a mozilla account it will import that into the new Ubuntu installation without affecting the existing installation from which it is taken. if you import nothing your Ubuntu and XP install will be fine also.

Re:-
Thankx, i'll try to do in that way but will there be errors in XP? should i back up first and proceed because i have lot of data in C drive(XP)?

---

### Post by presence1960 on 2009-08-18
> **masthijohna said:**
> Re:-
Thankx, i'll try to do in that way but will there be errors in XP? should i back up first and proceed because i have lot of data in C drive(XP)?

you should always back up your data prior to any OS installation and/or partitioning. Although the installer works almost 100% of the time you can't chance your data being lost to an unforseen event. 

You should get into the habit of backing up your data on a regular bais anyway. There are many programs that allow you to run a complete backup the first time then incremental backups thereafter.

Your XP will be safe, it is just that you are not getting an option to import an account from XP into Ubuntu.

P.S. make sure you have defragged XP at least once or twice prior to attempting the installation. This will make the resizing of XP's partition go smoothly.

---

### Post by LewRockwell on 2009-08-18
> **masthijohna said:**
> Re:-
Thankx, i'll try to do in that way but will there be errors in XP? should i back up first and proceed because i have lot of data in C drive(XP)?

if your data is not backed-up then you should IMMEDIATELY ABORT any changes to your hard drive

a proper ubuntu installation will do nothing to XP other than to possibly reduce the windows partition so that another partition can be created for ubuntu

still, we highly recommend:

that those unfamiliar with ubuntu first try out the LiveCD

then learn the particulars of partitioning and how to do this before the ubuntu installation

then learn the particulars of the grub bootloader if they desire to dual or multi-boot

then install ubuntu

.

---

### Post by presence1960 on 2009-08-18
> **LewRockwell said:**
> if your data is not backed-up then you should IMMEDIATELY ABORT any changes to your hard drive

a proper ubuntu installation will do nothing to XP other than to possibly reduce the windows partition so that another partition can be created for ubuntu

still, we highly recommend:

that those unfamiliar with ubuntu first try out the LiveCD

then learn the particulars of partitioning and how to do this before the ubuntu installation

then learn the particulars of the grub bootloader if they desire to dual or multi-boot

then install ubuntu

.

+1 Lew!
here are some links to get you (OP) up to speed:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

[http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/) -for a pdf ubuntu pocket guide which BTW has a great step by step on installing ubuntu

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by masthijohna on 2009-08-19
Thankx for the replies, i also want to know whether XP can be restored or repair using 
Ubuntu? Once i tried to install ubuntu in one of my friend's machine and Ubuntu setup was quit in the middle and when i restared the machine a file in XP(hal.dll) was missing and couldn't restore it using safe mood.So, any one knows how to restore or repair XP using Ubuntu.I have back up the XP(using Norton ghost) and if XP corrupted how can i restore/ repair XP?

---

