---
title: "Ready to finally dual boot.. need help"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by Proto_Blaze on 2010-08-28
im using windows 7... i also heard ubuntu has issues with ati graphics cards... but i want to run run it from a flash drive.. can i update ubuntu with codecs and designs when its on the usb? how do i get it to work with an internet card (sprint) any things i need to do when i run it?

---

### Post by sikander3786 on 2010-08-28
You can do a full install on a Flash Drive and that can be updated and further customised as well. The method of installation is clearly mentioned below.

For the internet card I don't understand which card you mean. Is it the regular ethernet card or something else?

> **C.S.Cameron said:**
> You can do a Full install to a stick 4GB and over, This will be updateable just like a hard drive install but you can not use the stick to easily install ubuntu to another machine.
Or you can use the start up disk creator from the Live CD and  select the persistent option that will save most changes. It will not allow kernel upgrades. You need a 1GB stick for the basic install and 2GB or larger for a persistent install. Persistence files are limited to 4GB.

Full install:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu 10.04.
Fill in "Time Zone" and "Keyboard layout".
At "Prepare disk space" select "Specify partitions manually (advanced)".
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
Click "Forward".
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Select Install.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you select the "Advanced" button and choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your hard drive, even when booting another computer.

---

### Post by Proto_Blaze on 2010-08-28
i use a wireless air card from sprint that gives me internet... also the flashdrive is temporary.... til im ready to make the dual boot

also to dual boot with windows 7... all i have to do is partition the hard drive... make a live flash drive... then install on the partition? (without problems happening)

---

### Post by sikander3786 on 2010-08-31
I am not sure about the wireless card. Let someone else answer that portion.

You have to undergo the same process you mentioned in your post for dual booting. Don't partition the hard driver in Windows, just free up some space i.e, don't create any partition on the free space and then you'll be able to select "Use the largest continuous free space" option during Ubuntu install which will do partitioning itself. And I hope all goes well and you'll be dual booting.

Sorry for the late reply.

---

