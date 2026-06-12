---
title: "Grub Rescue prompt"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by vishrut_n_shah on 2011-01-04
Hello ,

  I am having grub rescue prompt and not able to boot the system. Commands like help,insmod,kernel,root,reboot and configfile are not working.Only ls is working and showing all the partitions like (hd0,1),(hd0,7) etc.

Actually i was having two ubuntu 9.10 in (hd0,5) and (hd0,7) along with Windows7 in other partition.From windows7 i deleted partition having one of the ubuntu and now i am having this problem.

I also tried to run live ubuntu 8.04 and 10.04 but they are also not starting, i just get a blank screen.


Now how to recover my system from grub rescue prompt???

Help please.

Thanks in advance.

---

### Post by wilee-nilee on 2011-01-04
You will have to boot from a live cd unless you can manually boot in. You probably removed the Ubuntu that was in control of the boot.

So find the per-session boot menu key prompt. There is a out of the bios boot from menu that works when a straight cd first in the bios doesn't. My key is f12 pecked on like you do when powering on to get to the bios. Yours may be another f key or the esc key.

If you get in run this command in the terminal and post the results. Here is a link that goes with this command to reinstall grub2 from the live cd,rather then posting if you understand it.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
```
sudo fdisk -lu
```
[B]
Manual boot from grub prompt for grub2[/B]
set root=(hd0,X)    X=the partition # of OS 
linux /boot/vmlinuz(tab=kernel) root=/dev/sdaX 
initrd /boot/initrd(tab, then enter) 
boot (enter)

If you get in this way just run in the terminal.
```
sudo grub-install /dev/sda
```
then 
```
sudo update-grub
```

sda is correct if that is the hard drive so run the first command sudo fdisk -lu to confirm the drive letter.

To boot into the live cd and use it reload grub2 you have to be using a cd, that is equal to the install.

---

### Post by Linyx on 2011-01-04
[SIZE=2]You are using Grub or Windows Boot-loader....?

Ok,so right now you have one Ubuntu and Windows and you are not able to boot to any one,....

Two methods you can do for that..if you want to use **grub **so Go to Live-Cd and install it, but from your post it seems that you are not able  to Enter live-session now,

Method 2nd:-
                    If you have windows-7 repairing disk ,enter that CD and enter the **COMMAND-PROMPT** their and write "**bootrec.exe /fixmbr**" 

                                                      "**bootrec.exe /fixboot**"

This will Give you your Windows back at Boot-menu...if you haven't windows-7 DISK, Download Repair Disk free > [/SIZE][http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

[SIZE=2]Now if you have windows, a good tool for Configuring-Boot and **menu-Entries** > **EasyBCD** > [/SIZE][http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) , [SIZE=2]Now you can add Linux and many more entries at boot menu[/SIZE]...............

[SIZE=2]Good luck :p[/SIZE]

---

### Post by wilee-nilee on 2011-01-04
This is a grub prompt without the cd and (hd0,5) and (hd0,7) are mentioned so probably not a wubi.

Blank screen sounds like the cd is booting but the graphic driver is not working. So boot the equal cd to the install hold down the shift key immediately, if it is lucid or maverick earlier distros it might be the esc key.

If you get the menu to try, or install...etc hit f6 tick nomodeset then hit crtl+x to boot. then follow my first post.

---

### Post by vishrut_n_shah on 2011-01-05
Thank you for your suggestion but we didn't able to boot from live CD of ubuntu.


But we have solved it vie booting from FLASH Drive with TinyCoreLinux and installed grub again...

---

