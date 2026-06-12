---
title: "Problems with Bootable Ubuntu"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by simp1eton on 2010-07-16
Hi all,

I have recently downloaded the 10.04 ubuntu livecd and installed it onto my USB drive with unetbootin. 

However, I have some problems that I hope you people can help me with.

It seems that everything I downloaded and installed (such as g++, geany) gets deleted whenever I restart. Also, I also tried creating some test folders and test files, but they also get deleted whenever I restart the computer. Can someone help me and tell me what I can do to solve this problem? Thanks!

---

### Post by nothingspecial on 2010-07-16
Afaik unetbootin doesn`t have the ability to make a persistant live usb stick

From your unetbootin stick install usb-creator and use it to make a persistant usb ubuntu install on another stick.

---

### Post by C.S.Cameron on 2010-07-16
This is how I made a Unetbootin install to flash drive persistent.
(But it is easier to just to use usb-creator as mentioned above)
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext3 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Windows, started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, booted thumbdrive.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.

---

