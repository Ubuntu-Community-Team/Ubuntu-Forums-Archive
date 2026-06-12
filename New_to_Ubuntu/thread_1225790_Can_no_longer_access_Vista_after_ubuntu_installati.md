---
title: "Can no longer access Vista after ubuntu installation"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by pancho2 on 2009-07-28
Hi, I'm obviously an absolute newbie on ubuntu, but I can't access my Windows Vista account anymore after having installed ubuntu. Can anyone tell me how to re-access it? Or did I delete it by accident? Please, help out an utter newbie!

---

### Post by cozmicharlie on 2009-07-29
> **pancho2 said:**
> Hi, I'm obviously an absolute newbie on ubuntu, but I can't access my Windows Vista account anymore after having installed ubuntu. Can anyone tell me how to re-access it? Or did I delete it by accident? Please, help out an utter newbie!

Don't panic - it is most likely just a problem with the boot loader.  As long as you did not erase the vista partition it is very easy to get back to the Windows boot loader (MBR).

First we need some info.  The Ubuntu installer offers a number of options for partitioning the hard drive.  When you installed Ubuntu, how did you partition the hard drive?  In Ubuntu, can you access your vista files? If so then you have not deleted vista.  

Normally, Ubuntu installs a boot loader called grub.  Grub should recognize all your installed operating systems and show a list at boot up.  All you do is scroll to the OS (in your case vista), hit enter and you should boot to Vista.  If not then you can restore the vista MBR using the install disc as described here:
[http://www.winvistatips.com/fix-mbr-t116.html](http://www.winvistatips.com/fix-mbr-t116.html)

---

### Post by nhasian on 2009-07-29
can you describe how you installed ubuntu?  did you

a) boot into windows and then insert the cd into the drive to install ubuntu inside of windows (this is the wubi method)

or

b) boot off the liveCD and overwrite your windows partition?

If you previously shrink the windows partition to make some room for ubuntu and THEN booted off the liveCD you could have selected the empty partition to install ubuntu to...

open up a terminal from applications->accessories->terminal and give us the output from the followign command:

```
sudo fdisk -l
```

---

### Post by pancho2 on 2009-07-29
I did the sudo fdisk -l command and got this. I get the feeling this is bad news.

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51645164

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37707   302881446   83  Linux
/dev/sda2           37708       38913     9687195    5  Extended
/dev/sda5           37708       38913     9687163+  82  Linux swap / Solaris
mike@mike-laptop:~$

---

### Post by pancho2 on 2009-07-29
[quote=nhasian;7696239]can you describe how you installed ubuntu?  



I did A, I originally had Vista installed and then installed ubuntu.

---

### Post by bumanie on 2009-07-29
It looks as though you have overwritten your vista installation, there is no indication of vista being on the hard drive any longer.

---

### Post by hibliss on 2009-07-29
From your fdisk -l, it looks like you told Ubuntu to use the entire disk during install. I no longer see an NTFS partition, looks like Vista was formatted by the installer and is gone for good, or at least your data is.

---

### Post by pancho2 on 2009-07-29
Is there any way to at least restore Vista?

---

### Post by EvilMarshmallow on 2009-07-29
Nope.  The best you could do is to start over from scratch... install Vista on half your hard disk (thereby destroying Ubuntu), and then reinstall Ubuntu, being careful not to overwrite the vista partition you just created.

---

### Post by LewRockwell on 2009-07-29
> **pancho2 said:**
> Is there any way to at least restore Vista?

If you lost data that you would be willing to spend money to retrieve then you might first want to review this:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Testdisk is included in the Parted Magic LiveCD Utilities Disk

[http://partedmagic.com/](http://partedmagic.com/)

.

---

### Post by presence1960 on 2009-07-29
> **EvilMarshmallow said:**
> Nope.  The best you could do is to start over from scratch... install Vista on half your hard disk (thereby destroying Ubuntu), and then reinstall Ubuntu, being careful not to overwrite the vista partition you just created.

No, NO , NO!!. Why would you make him uninstall a perfectly good ubuntu install? All he needs to do is boot the Ubuntu live CD and use gparted (Partition Editor) to shrink  sda1 (Ubuntu /) to create space for vista. He can then boot the Vista install DVD and install to that space. After vista is installed he can restore GRUB like this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

The only reason to install Vista over ubuntu is if the OP only has a recovery DVD/partition as that will format the entire hard disk as NTFS.

Why do we insist on telling people that they have to remove an Ubuntu install to install windows? That is completely erroneous except in the instance I mentioned. here are some links to back me up:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

come on people, why are we going to make someone go through all the work of installing 2 OS's when one is already installed and working. let's increase our knowledge and usefulness by staying abreast of things.

---

