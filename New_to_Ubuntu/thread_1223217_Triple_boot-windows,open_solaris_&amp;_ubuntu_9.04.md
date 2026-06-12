---
title: "Triple boot-windows,open solaris &amp; ubuntu 9.04"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by guitsy on 2009-07-25
Hi Friends

here iam going to explain how to install 3 operating system.

assume that we have a 40GB harddrive and we r givin equal space for each operating system  ie 13.3 GB .

First install windows.during installation make two equal partition of 13.3 gb...(ex...C:DRIVE(13.3)....D:DRIVE(13.3))and leave 13.3 free space.
install windows in c drive.complete the installation..

next put the open solaris cd... and during installation choose the option..unused portion....and enter 13.3 in the disk space option...
(13.3 is the space which we left unused during windows installation). 
complete the installation....& restart.

during the boot choose windows operating system again.
In windows go to MY COMPUTER...right click ur mouse and choose MANAGE...choose DISK MANAGMENT and choose the D:DRIVE...........right click and choose DELETE LOGICAL DRIVE(ie....D:drive).delete it.....restart.

put the ubuntu cd...in the partition option..choose ..manual partition..
now choose the free space....(13.3gb)right click and choose new partition..in the partition table PLEASE note down the path of other two operating system.......ie.../sda1(windows)..../sda3(open solaris).

choose..... @LOGICAL.
in the disk space put the space double your computer memory(ie.......if u r havin...256mb mem.......put  around 550MB range of space...)
nxt  choose.......@BEGINING....
nxt   choose......SWAP AREA.

DONE....again go back to free space in  the partition table....right click it.....choose new partition
choose........@PRIMARY......if u dont see any options don't worry..just continue
nxt......in the disk space.....enter the value....... &leave 3GB/3000MB free space for nxt partition.
nxt.........choose........@BEGINING
nxt.....choose........EXT3
In ......mount point....choose  /

DONE....again go back to free space in  the partition table....right click it.....choose new partition
choose........@LOGICAL
nxt......in the disk space.....enter the value 3000MB.
nxt.........choose........@BEGINING
nxt.....choose........EXT3
In ......mount point....choose  /home
DONE....

Now let me explain exactly how the partition done with 13.3GB space.
SWAP AREA-550MB........(...for 256mb of ram)
PRIMARY-9750MB...for..../
3000MB...for...../home
now install ubunntu..........complete the installation and restart..

choose ubuntu from  grub menu
in ubuntu go to application-terminal.and type
sudo nano /boot/grub/menu.lst
search down and find the _other operating system_ options.add the following after the chainloader+..

title opensolaris
rootnoverify(hd0,2)
chainloader +

now press ctl-x and y.
restart..u will b able to see   and work with 3  operating systems ......thnks

---

