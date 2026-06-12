---
title: "ubuntu 9.04 + XP dual boot"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by bishal86 on 2009-08-12
First of all i am completely new to ubuntu. i haven't used it before and would like to try it. i want to have a dual boot of XP and ubuntu 9.04. i have a couple of tutorials on how to do that but i am still confused.
i have already partitioned my hard drive. i use C for XP and D,E,F,G for storing other files and documents. i would like to install ubuntu on D. 
can anyone help me how to do it?

---

### Post by jonathanysp on 2009-08-12
well first you can just put in the ubuntu liveCD and the select install (don't worry, it will confirm all your settings and preferences before actually writing anything to the hard drive) When you reach the partitioning section, simply select the partition that you want to install ubuntu on. However, the partitions will not be labeled C, D, E or F but something like /dev/sda1 you will have to note down the size of D partition and match it up with the choices you see during installation. Once you have selected it properly, the livecd will automatically detect your windows installation and allow you to dualboot when the installtion is complete

---

### Post by NightwishFan on 2009-08-12
I was going to suggest WUBI, however since you are pre-partitioned a dual boot installation should be easy. It will delete all data on the Ubuntu partition, please note.  Ubuntu will be able to access your Windows drives. A dual boot setup will be automatically added to the boot menu.


If you want to 'remove Ubuntu and have only Windows' you will need to blank the partition Ubuntu is on, and repair the Windows boot loader (MBR). Tools are available to do this.

---

### Post by bishal86 on 2009-08-12
alrite thanks guys but one more thing D,E,F on my drive have equal spaces so how do i know which one is /dev/sda1?
and will i be able to install network drivers, display drivers for nvidia and realtek sound drivers?
and i have read about this swap. do i have to do something about it?

---

### Post by NightwishFan on 2009-08-12
The partitioner will inform you. If your partitions are in physical order, then C will be on the left, D just to the right.

You can check partitions from Windows by using the disk utility. Right click 'My Computer' icon and click **Manage**.

---

### Post by bishal86 on 2009-08-12
and what about the drivers and "swap"? do i need to worry about swap?

---

### Post by NightwishFan on 2009-08-12
Ubuntu should use a special type of extended partition to group the ubuntu and swap drives. You can select the partition you want to use during the installation. If you delete the D drive and have it be free space, just tell Ubuntu to install in the largest free space, though I am not sure if that is needed in Jaunty. It might just ask which partition to use. 

I am not sure if it does since I always pre-partition.

When you get to the partitioning step of the installation, just have someone on here verify you have it set up right before you finish the step.

---

### Post by bishal86 on 2009-08-12
i got confused when i tried to install. in the partitioning step which option do i select:
install side by side with xp or manually select the drive?

---

### Post by NightwishFan on 2009-08-13
Hi, could you post a screenshot of your partition setup if you select install side by side?

---

### Post by ramoj02 on 2009-08-13
You don't have to make a partition if you want to dual boot Windows and Ubuntu if you use Wubi. Wubi is a program that installs Ubuntu on your computer without partitioning you hard drive. For me, it's the easiest way to get Ubuntu. You can get Wubi at [http://www.wubi-installer.org](http://www.wubi-installer.org)

Here's the wiki for Wubi:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by alexlafreniere on 2009-08-13
> **bishal86 said:**
> and what about the drivers and "swap"? do i need to worry about swap?


I can almost guarantee all the drivers you need will be installed by Ubuntu for you. You can check to see what works and what doesn't in the LiveCD. If it works then, it'll work when you install it to your disk. As for nVidia drivers, you will get a separate prompt after you install, because nVidia keeps their drivers closed source, so they are labeled as "restricted" and must be explicitly enabled. Don't worry though, Ubuntu will simply prompt you to enable them and you're off to the races.

---

### Post by jesse100 on 2009-08-13
I have tried to get wubi to install on my eee winxp and it will not. What gives?

---

### Post by bishal86 on 2009-08-14
Thanks to all of u guys i have successfully installed ubuntu and i am loving it.
i used manual selection of drive and formatted my D and installed in it using ext4 file system.
i see that xp now doesn't recognise D drive, is it normal?

and i would also like to edit the bootloader to select xp as default and increse the time to 30 secs. how do i do that?

---

### Post by egalvan on 2009-08-14
> **bishal86 said:**
> 
i used manual selection of drive and formatted my D and installed in it using ext4 file system.
**i see that xp now doesn't recognise D drive, is it normal?**

Yes, Microsoft has no knowledge of other file systems such as ext3 or ext4.
There ARE drivers available to allow MS to see ext2 style file systems.


> and i would also like to edit the bootloader to select xp as default and increse the time to 30 secs. how do i do that?

Type this code into a terminal...


```
gksudo gedit /boot/grub/menu.lst
```

the relevant portion is like this

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR="Red"]timeout		30[/COLOR]

```


As for changing the default,

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# [B]You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.[/B]
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
[COLOR="Red"]default		saved[/COLOR]
```

along with this,

```
title		WinXP Pro
root		(hd0,0)
[COLOR="Red"]savedefaul[/COLOR]t
makeactive
chainloader	+1

```


or use StartUpManager, which is a GUI interface that allows you do make several changes to the startup sequence.
You may need to install this...

---

### Post by bishal86 on 2009-08-14
thanks a lot.
i think i already have startup manager.

---

### Post by bishal86 on 2009-08-27
Hi i want to replace my XP with windows 7 keeping jaunty intact. how do i do this? 
i have XP in C and jaunty in D currently. i want to remove XP and have windows 7 in C.

---

### Post by parrotred on 2009-10-08
i have a 3 hard disk
primary master as 60 gb seagate windows
primary salve 160 gb seagate data single ntfs partition
secondary master dvd-ram lg gh22
secondary slave 20 gb samsung ubuntu jaunty


I first installed windows and then unplugged that hard disk and installed ubuntu.
I have been using the system by removing either hard disk but now i would like to use both windows and ubuntu as dual boot.
i tried the following

sudo dd if=/dev/sdc1 of=bootsect.lnx bs=512 count=1 
i copied the bootsect.lnx from dev/home to the ntfs partition and then removed the ubuntu cable and logged in windows and than copied the bootsect.lnx to c drive and modified the boot.ini with following
c:\bootsect.lnx="Linux UBUNTU"

This did not work

so i tried this
sudo dd if=/dev/sdb1 of=bootsect.lnx bs=512 count=1 
i copied the bootsect.lnx from dev/home to the ntfs partition and then removed the ubuntu cable and logged in windows and than copied the bootsect.lnx to c drive and modified the boot.ini with following
c:\bootsect.lnx="Linux UBUNTU"

This did not work


Please guide me what should i do in order to dual boot with windows xp as the main and ubuntu as second.

---

### Post by presence1960 on 2009-10-08
> **parrotred said:**
> 

This did not work


Please guide me what should i do in order to dual boot with windows xp as the main and ubuntu as second.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Kapitän Rotbart on 2009-10-08
> **bishal86 said:**
> Hi i want to replace my XP with windows 7 keeping jaunty intact. how do i do this? 
i have XP in C and jaunty in D currently. i want to remove XP and have windows 7 in C.

Probably best to wait for Karmic's release...which is just days after win7's release.

Install win7 over winxp (C:\). Then install Karmic over Jaunty (D:\). Easy as pie!

---

