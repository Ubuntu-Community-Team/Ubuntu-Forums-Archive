---
title: "live usb ubuntu related question"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by ornothaloapq on 2010-07-17
i am funning ubuntu from a live usb drive session.
my question is, is it possible to mount the usb drive and save things like word document to it. right now i cant see the usb drive from my computer in the "places" menu.
is there a way to accomplish this?

---

### Post by C.S.Cameron on 2010-07-17
Are you running a persistent install, (usb-creator)?
Have a look in filesystem/cdrom, this should be the root of your USB drive.

This is where things will be accessible if you plug it into a windows machine.

---

### Post by Chaosr3aper on 2010-07-17
i run ubuntu off of my usb as well. is there anyway that i can save file onto the flashdrive with my OS and keep the files there the next time i boot of linux. right now i can dl anything i want but if i shut down the pc and move the usb i look everything except the base OS

---

### Post by techunit on 2010-07-18
yes you can checkout [URL="http://pendrivelinux.com/"]http://pendrivelinux.com
[/URL]
there universal installer will allow you to save the files right to the thumbdrive... 

I have made a Video Tutorial on Creating One...

[This link covers creating one in both windows or ubuntu]("http://ubuntuvideotutorials.wordpress.com/category/utilities-2/bootable-flashdrive/")

---

### Post by C.S.Cameron on 2010-07-18
> **Chaosr3aper said:**
> i run ubuntu off of my usb as well. is there anyway that i can save file onto the flashdrive with my OS and keep the files there the next time i boot of linux. right now i can dl anything i want but if i shut down the pc and move the usb i look everything except the base OS

If you install to flash drive using usb-creator there is an option to make the disk persistent.
The size of the persistence file is limited to 4GB by the FAT32 file system.
If this is not enough:

Boot Live CD.
Plug in flash drive.
Start Partition Editor
Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional)
Create a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk / syslinux / text.cfg and added "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.
You are persistent.

---

### Post by janderek on 2012-06-09
Try using pendrivelinux. Pendrivelinux provides simplified information to make it easy for anyone  to install, boot, and run their favorite Linux Distro from a portable  flash drive. You can boot your OS through USB. To read more about this try looking here : [http://www.techyv.com/questions/how-install-ubuntu-linux](http://www.techyv.com/questions/how-install-ubuntu-linux)

---

