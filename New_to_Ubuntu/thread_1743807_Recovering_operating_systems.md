---
title: "Recovering operating systems"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by RobikShrestha on 2011-04-29
I have windows 7 on c:
I have ubuntu 10.04 on sda 7
I did something stupid:
zcat boot.img.gz /dev/sda
Then it tried to install ubuntu 6
Then I used super grub.
I tried every option available.
For GNU/LINUX, it says file not found. (eg: menu.lst)
For windows, it just does nothing.
I am in a big mess. What should I do? Please help!!!!!!
I do not have a live CD or USB.

---

### Post by jcolyn on 2011-04-29
Since you obviously have internet connection why not download the ISO and burn a live CD.. You should then be able to run ```
sudo update grub
```

---

### Post by RobikShrestha on 2011-04-29
My bandwidth is limited and we have power cut offs of 7 hours. i.e. there is power for only 4 hours. I can't even buy a live cd because it's not available in the market. I am downloading "damnsmall linux" from unetbootIn. If I could run that on laptop, I could download iso. But I do not know how to use that OS. Is there another way out??

---

### Post by lkraemer on 2011-04-30
If you have a CD/DVD of Windows 7, then this will get your Windows 7
booting.
[http://windows7themes.net/how-to-fix-mbr-in-windows-7.html](http://windows7themes.net/how-to-fix-mbr-in-windows-7.html)

If you don't have a Windows 7 CD/DVD, then you need to use a Recovery
Partition to do the same.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Or you can use Ubuntu LiveCD to do it as per:
[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

I would suggest booting from the Ubuntu LiveCD, then install the attached 
deb file on your LiveCD system by double Left clicking on the tar.gz to extract the deb to your desktop.
Then double left click on the deb to install it, and proceed as follows from a Terminal:

```

sudo fdisk -l

```
That will list the available partitions. You&#8217;re looking for a partition that says something like.......
```

    /dev/sda1 1 9327 74919096 83 NTFS

```
It could be hda1 or some other designation.............

The two important bits are the &#8216;/dev/sda1&#8216; which is the partition itself and the &#8216;NTFS&#8216; which tells
us it&#8217;s a Windows formatted partition.  So your Windows partition exists on your drive **sda** and
it&#8217;s on partition 1. The MBR for drive **sda** (assuming you boot into windows using it&#8217;s native
boot loader) is what you want to repair.

**ms-sys usage:**
```

Usage:
	ms-sys [options] [device]
Options:
    -1, --fat12     Write a FAT12 floppy boot record to device
    -2, --fat32nt   Write a FAT32 partition NT boot record to device
    -3, --fat32     Write a FAT32 partition DOS boot record to device
    -4, --fat32free Write a FAT32 partition FreeDOS boot record to device
    -5, --fat16free Write a FAT16 partition FreeDOS boot record to device
    -6, --fat16     Write a FAT16 partition DOS boot record to device
    -l, --wipelabel Reset partition disk label in boot record
    -p, --partition Write partition info (hidden sectors, heads and drive id)
                    to boot record
    -H, --heads  Manually set number of heads if partition info is written
    -7, --mbr7      Write a Windows 7 MBR to device
    -i, --mbrvista  Write a Windows Vista MBR to device
    -m, --mbr       Write a Windows 2000/XP/2003 MBR to device
    -9, --mbr95b    Write a Windows 95B/98/98SE/ME MBR to device
    -d, --mbrdos    Write a DOS/Windows NT MBR to device
    -s, --mbrsyslinux    Write a public domain syslinux MBR to device
    -z, --mbrzero   Write an empty (zeroed) MBR to device
    -f, --force     Force writing of boot record
    -h, --help      Display this help and exit
    -v, --version   Show program version
    -w, --write     Write automatically selected boot record to device

    Default         Inspect current boot record

Warning: Writing the wrong kind of boot record to a device might
destroy partition information or file system!

```	    
ms-sys can write new MBR code to your disk. Type 'ms-sys -h' to obtain some help on the different parameters,
but in most cases you run it first to analyse your disk. 'ms-sys /dev/hda' or 'ms-sys /dev/sda', will tell
you about your MBR.
'ms-sys -m /dev/hda' will write an XP style MBR to your disk.
Remember that this utility deals only with the MBR. 


The Version I've attached isn't the latest and doesn't support Windows 7, but as
per postings and remarks it should get Windows 7 booting.  You may want to boot
from LiveCD, then install the necessary items to compile the latest version and
compile it, making a deb.

**INSTALL REQUIRED SOFTWARE FOR COMPILE:**
Typically you need to install build-essential and the headers for the
kernel you are running, if you are going to compile code.
```

uname -r

```
will tell you the kernel you are currently running.
```

sudo apt-get install build-essential linux-headers-$(uname -r) gettext checkinstall

```
will install the software needed to compile your code.


**DOWNLOAD the Source:**
[http://sourceforge.net/projects/ms-sys/files/ms-sys%20stable/2.2.1/ms-sys-2.2.1.tar.gz/download](http://sourceforge.net/projects/ms-sys/files/ms-sys%20stable/2.2.1/ms-sys-2.2.1.tar.gz/download)
from sourceforge.net


**TYPICAL COMPILE STEPS: (from within your source directory)**
```

./configure
make clean
make
sudo make install

```
"make clean" won't remove anything on the first compile, but will clean up
on a successive compile.  For ms-sys you won't need all the above commands....

You can also use checkinstall to build a deb file.
The commands I used were:
```

cd Desktop
cd ms-sys-2.2.1/
make clean
make
sudo checkinstall -D

```
Which made a deb file for Debian 6.0 - 64 Bit.  If your system will boot a LiveCD of Debian 6.0 - 64 Bit,
or Ubuntu 64 Bit, you can use the attached deb to install the Windows 7 MBR.................


We want to fix the MBR on /dev/sda. To do so, type the following:
sudo ms-sys --mbr /dev/sdX (or whatever your drive is, to find that out type sudo fidsk -l)....in our case it is:
```

sudo ms-sys --mbr /dev/sda

```
or 
```

sudo ms-sys --mbr7 /dev/sda

```

Then reboot your system, and remove the Ubuntu LiveCD.
That should get your windows booting...............

Once windows is booting, you may also have to boot the Ubuntu LiveCD to update grub to get Ubuntu booting.

ms-sys is the i386 - 32 bit version of 2.1.0-1
ms-sys_221 is the 64bit version of 2.2.1 Compiled on Debian 6.0 - 64 Bit
ms-sys_221_i386 is the 32 Bit version Compiled on Ubuntu 10.04

**Another option** is to download the **Trinity Rescue LiveCD** and use ms-sys from that RescueCD.
[http://trinityhome.org/Home/index.php?content=TRINITY_RESCUE_KIT____CPR_FOR_YOUR_COMPUTER&front_id=12&lang=en&locale=en/](http://trinityhome.org/Home/index.php?content=TRINITY_RESCUE_KIT____CPR_FOR_YOUR_COMPUTER&front_id=12&lang=en&locale=en/)
[http://trinityhome.org/Home/index.php?content=3.4_BOOTSECTOR_REPAIR_1&front_id=12&lang=en&locale=en](http://trinityhome.org/Home/index.php?content=3.4_BOOTSECTOR_REPAIR_1&front_id=12&lang=en&locale=en)

Also, MBRFix.............

So, there are lots of options................GOOD LUCK!  Keep us informed........
 
lk

---

### Post by RobikShrestha on 2011-05-01
ok I got live Cd of ubuntu 10.04
I did
sudo apt-get install grub
when i did 
grub> 
find /boot/grub/stage1 
It says: error 15: file not found
I am sure that is because i had done: zcat boot.img.gz /dev/sda to ruin my computer at the first place
I know my ubuntu was on sda7 but I do not know its hd no. that is hd0 or hd1 or what??
What is the next step?

editted:
When I opened gparted:
It showed: 289 GB unallocated space.
I am so screwed, I do not how that happened, I haven't formatted or anything. Now what?

---

