---
title: "How Can I Disable Automount of a Specific Drive on Startup?"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by the137 on 2011-07-13
Did some searching, every answer I've found either disables automount entirely, requires editing fstab (which doesn't contain anything about this specific drive) or simply doesn't work

pysdm seems to be the popular answer, but isn't working for me. Might be because I have a weird setup.  

Long and short of it is I've got a primary linux os installed on the internal hdd, and natty 11.04 on a usb external. I want to prevent the internal drive from ever mounting when running natty.   

fstab doesn't list the drive at all, just the partitions on the external 

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# /var was on /dev/sdb5 during installation
UUID=89c9aaa7-d890-4c0f-822a-9f9528619cb5 /var            ext4    defaults        0       2system / administration / disk utility lists my external as sda1 (primary) (and yes im running gnome 2.3, and ill be back to kde once i figure that out :P )

Lastly, pysdm lists the drives (sda / sdb) but wont expand and all options are grayed out even when i have a drive highlighted. I installed it thru apt-get, tried uninstalling reinstalling restarting etc.. .

Kinda stuck here... any kind OGs that want to lend a hand?

:KS:KS:KSGold star for the first answer that works :KS:KS:KS

---

### Post by mikejonesey on 2011-07-13
where is this drive bein auto mounted to and what is it's udev id and uuid, are you saying your external sda1 is auto mounting? strange that it's sda1 external...

for when you reply somthing along these lines in the stab would work;

/dev/udev-id /media/extern-drive-noauto ext4 user,noauto 0 0

to mount all drives in stab at any point;

mount -a

---

### Post by the137 on 2011-07-13
> **mikejonesey said:**
> where is this drive bein auto mounted to and what is it's udev id and uuid, are you saying your external sda1 is auto mounting? strange that it's sda1 external...

its being mounted to /media/ee8f663c-37b3-4223-9f05-93ed8a45db55

how do I find the uuid and the udev id? the only place I know to look is disk utility

thanks for the quick response

and not quite, the external is whats running ubuntu, its the internal thats automounting.

---

### Post by mikejonesey on 2011-07-13
ee8f663c-37b3-4223-9f05-93ed8a45db55 is uuid so;

UUID=ee8f663c-37b3-4223-9f05-93ed8a45db55 /media/ee8f663c-37b3-4223-9f05-93ed8a45db55  ext4 user,noauto 0 0

this would mean it is not aut mounted but standard users can mount it...

---

### Post by the137 on 2011-07-13
add that to fstab?

edit:
UUID=ee8f663c-37b3-4223-9f05-93ed8a45db55 /mnt/internal  ext4 admin,noauto 0 0

if I add the line like this am i correct to assume that it'll mount it to a new spot and require the root password to mount?

---

### Post by mikejonesey on 2011-07-13
yes it's not mounted till that link is clicked...

to eliminate the listing... you could try options like owner,uid=0 then only root could mount it so it may be dropped from the list as a std user...

eg

```
UUID=ee8f663c-37b3-4223-9f05-93ed8a45db55 /media/ee8f663c-37b3-4223-9f05-93ed8a45db55  ext4 uid=0,owner,noauto 0 0
```

---

### Post by mikejonesey on 2011-07-13
to check what drives are currently mounted;

mount | grep ^/dev

---

### Post by the137 on 2011-07-13
Thanks for not quoting the stupidity thar...

btw i appended the fstab file and its gone from the drop down menu so heres your gold star as promised ;) :KS

any way to up rep on here or anything similar? 

thanks again for the help

edit: I missed the space before ^/dev , works great now ty

---

### Post by the137 on 2011-07-13
this is what Ill be reading tonight, throwing it in here just in case someone finds this thread in search 

> The /etc/fstab file is used by some programs to determine file system  types and mount points. If you are new to linux, configuration files can  seem cryptic and intimidating. This tutorial contains an example  /etc/fstab file broken down and thoroughly explained. Keep in mind that  the sample that is broken down and explained is larger than your typical  /etc/fstab so that this tutorial can be applicable to a wider audience.  I also included the /etc/fstab from my personal computer.

EXAMPLE:

1 #device	mount point	file system	options		dump	check
2
3 /dev/hda1	/		reiserfs	defaults		0	1
4 /dev/hdb1	/home		ext2		auto,notail		1	1
5 /dev/hdc	/mnt/cdrom	iso9660	        defaults                0	0
6 /dev/hdd	/mnt/dvdrw	iso9660	        ro,users,noauto	        0	0
7 /dev/sda1	/usr		reiserfs	ro, owner		0	1
8 /dev/fd0	/mnt/floppy	auto		user			0	0
9 /dev/hda5	swap		swap		defaults		0	0
10 host:/var	/root/var	nfs		uid=0,gid=0		1	0
11 proc	/proc	proc		proc		defaults        	0	0

	The numbers at the beginning of each line of the example file are for  reference use of this tutorial. If line numbers were added to an actual  configuration files the result would be not being able to boot after the  next shutdown and the common “mount: can't find /dev/hde in /etc/fstab  or /etc/mtab” error message when you try to mount a file system.

	The first line of the example file is a comment, which is ignored by  the process reading the file. Commenting lines out in linux  configuration files is done by using the # character. Comments are very  useful for people reading or editing the file. In fact, this whole  tutorial could be contained inside a working, fully functional,  /etc/fstab file if the lines containing text explaining things were  commented out with #. The # character is universally used in linux  configuration files to identify comments. Many distributions include a  commented line at the beginning of the file to show what each column  defines.

	As you have more than likely noticed, the /etc/fstab file is divided  into columns. The first column defines the device file pointing to the  device with the file system to be mounted. The second column is the  mount point, or the directory where the file system can be accessed.  Column number three defines the file system type used on file system  being mounted. An important thing to remember about file system types is  that in order for you to be able to mount and use a volume, you must  have support for the file system type compiled into the kernel itself or  have a kernel module for it. Kernel issues are beyond the scope of this  tutorial. The fourth column is used for mount options. Some mount  options are file system specific. A chart has been included to explain  common mounting options. The fifth column is the dump column. It is used  by the dump utility to determine whether or not it should back up the  file system being defined. A 0 means it won't be backed up, and a 1  tells dump to back it up. This document will not go into the details of  the dump utility. The sixth column is the order fsck checks a file  system when the system is booted. A 0 in this column indicates fsck will  never check a file system. This value should be used for removable  media such as CD and floppy drives. Any value greater than one tells  fsck to check the file system at boot. The order they are checked is the  numerical order of values assigned in this column.

	The second line serves no purpose other than making it easier to read by someone editing the file.

	Line number three in this example is technically the only line you  absolutely must have, although you should never configure your system  this way if you want it to be stable. You should also define a swap  partition, which will be explained later. The reason this line is  necessary is because it defines the root directory to be mounted when  the system boots. Since other file systems are mounted in locations  within the root directory, logically you won't be able to mount any file  systems without a root directory defined. Mounting another file system  before mounting the file system designated to have the root partition is  like giving driving directions to use a road that hasn't been built  yet.

	Line number four defines a separate partition to be used as users home  directories. It is often wise to use a separate partition for home  directories. It preserves user preferences and files in the case of a  new installation or re-installation.

	Line number five defines an IDE CDROM drive, and line six defines  another optical drive. Typical mount options for optical drives are  user, users, noauto, ro, auto, and defaults. Defaults shouldn't be used  on workstations or personal computer systems because only root will be  able to mount a file system on a CD or DVD. 

	Line seven is an example of defining a SCSI partition.

	Line eight defines a floppy drive. As you probably notice the file  system type is auto. This means the system will attempt to automatically  detect the file system type the defined device uses.

	The ninth of the example file defines a swap partition. While not  mandatory, it is highly recommended to define a swap partition in  /etc/fstab. You should ALWAYS define a swap partition. Swap partitions  are nothing more than dedicated partitions used for virtual memory.  It  is also possible to use a file dedicated to virtual memory but it is  beyond this tutorial. Virtual memory is used when the kernel or  applications use up all of your systems RAM or move data there to clear  space in the immensely faster system RAM for other data.

	The second to last line of the example file shows an NFS mount. As you  probably noticed a device file isn't specified. In the column where the  device file is normally defined, the NFS server hostname and export  directory are specified. The uid=0, and gid=0 tells the computer to make  the group and user with the specified ids. In this example both the  group and user id are 0, which is the user root and group root. Mounting  file systems with specific user and group ids can be a useful security  or accessibility tool.

	Last but not least, is the proc file system. The proc file system is a  virtual file  system used by the kernel to store hardware information.  Some processes use it to retrieve information about hardware. If left  undefined the system will use space on whatever device is mounted as the  root partition.

	If this tutorial doesn't cover what you are looking for doesn't include  what you are looking for, I am going to point you in the right  direction on finding help. For file system specific mount options try  looking through the mount man and info pages. To access them type man  mount or info mount at any shell prompt. Another good source is the  Internet. Try searching for a web page using your favorite search  engine. Forums such as the one at linuxquestions.org are great places to  seek help. Your local bookstore might have some good linux books.

QUICK REFERENCES

column breakdown:

column	description

1		device file
2		mount point
3		file system type
4		mount option
5		fsck order
6		dump (1= backup, 0=don't backup)

common mount options:

option		definition

auto		automatically mounts at boot
noauto		doesn't automatically mount at boot
owner		only root or the owner of the device file can mount this file system
user		allows any user to mount a file system, only root or the user who mounted
		the file system can unmount it
users		same as user except any user can unmount it
ro		mounts the file system as read only
defaults	mounts the file system with the default options
uid=x		mounts the file system as user with id x (ownership)
gid=x		mounts the file system as group with id x (ownership)
noexec		prevents the execution of files on specified device

the /etc/fstab from my personal computer:

# /etc/fstab: static file system information.
#
# <file system> <mount point>	        <type> 	        <options>       <dump>  <pass>
proc            /proc                   proc    	defaultes	  0       0
/dev/hda8	/                       reiserfs	notail		  0       1
/dev/hda7	none            	swap    	sw		  0       0
/dev/hdc	/media/combo    	iso9660 	defaults          0       0
/dev/hdd	/media/cdrw     	iso9660 	ro,user,noauto    0       0
/dev/fd0	/media/floppy   	auto    	rw,user,noauto    0       0
/dev/hda1       /media/windows 	        ntfs 	   	user,ro,auto	  0       0
/dev/hda6       /media/media    	ntfs		user,ro,auto	  0       0
/dev/hda5       /media/games    	ntfs   		user,ro,auto	  0       0
/dev/hdb1       /media/storage  	ntfs   		user,ro,auto	  0       0

Any feedback regarding this document would be appreciated as I plan to  write more articles breaking down common configuration files.

The following copyright notice is to keep this document free as in  freedom, and price. It is also added to give credit where credit is due.

COPYRIGHT MARCH 2006 by Tyler M. Burns. This document may be distributed  electronically. This document may be used as a technical reference for  writing other documents. Printing is authorized as long as it isn't  published. This documents defines publishing as distribution of this  document in exchange for money or goods. This includes but is not  limited to books, magazines, and newspapers. Publishing is prohibited  unless hard copy, written permission is given by the author to the  person or organization wanting to publish this tutorial. Modifications  are allowed as long as they are released with this copyright, which must  remain unmodified. Modifications require the name and email address of  the author of the original document and author(s) of modified version(s)  if the modification is made to an already modified version of this  document. Modified  versions must note the modifications made.  Publishing of modified versions require the written permission of both  the original author and the author of the modification. Modifications  must contain at minimum the email addresses of the author of the  original documents and author(s) of modifications in the contact  information section below. Failure to provide contact information for  modifications will forfeit all rights to the author of the original  document. In the event the author and if applicable author(s) of  modification(s) do not respond to a request to publish this document,  this document may not be published. Appropriate legal actions will be  taken for any violation of this copyright.

Author: 

Name	Tyler M. Burns
Email	[EMAIL="tyler.m.burns@gmail.com?"]tyler.m.burns@gmail.com[/EMAIL]

---

### Post by mikejonesey on 2011-07-13
no rep stuff just a coffe rating depending on number of posts in the help sect...

---

