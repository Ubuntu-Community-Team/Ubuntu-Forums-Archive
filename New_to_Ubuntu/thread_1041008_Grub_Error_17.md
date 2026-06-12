---
title: "Grub Error 17"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by WesselPretorius on 2009-01-16
I have installed ubuntu 8.10 on an external hdd on a new partition. I have unplugged all my other hdd's so to boot only from my external. I have reinstalled ubuntu already once and it gave this error again after restarting from installation. 
Any Help Please?

---

### Post by WesselPretorius on 2009-01-16
I have been working forever on windows xp and have recently been starting to take a look at linux and especially ubuntu. I have been struggling a bit with the intallation due to a 'grub' error message.

I would like to know what exactly 'grub' is all about.

---

### Post by stevoo on 2009-01-16
[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)

 i am wondering what error do you have ?

---

### Post by WesselPretorius on 2009-01-16
error 17

---

### Post by Elfy on 2009-01-16
I use this page for my grub errors

[http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible](http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible)

If you need help then what doesn't boot - XP or ubuntu?

---

### Post by WesselPretorius on 2009-01-16
xp is fine, I unlpug my xp drive for 'data loss' reasons (don't wana have a booboo). But doesn't matter if it is in or not Ubunutu no work

---

### Post by Elfy on 2009-01-16
Perhaps then when you installed ubuntu it wrote the bootloader to the xp drive - you remove it and grub can't find what it needs to boot.

What happens if you leave the drive in and boot?

---

### Post by WesselPretorius on 2009-01-16
Still the same error. I removed before I installed ubuntu

---

### Post by Elfy on 2009-01-16
Can you leave both drives in and boot the live cd, open a terminal from the apps/accessories menu and run this command please - paste the output in a new post please

```
sudo fdisk -l
```

---

### Post by WesselPretorius on 2009-01-16
just did it gives me a list of things

---

### Post by Elfy on 2009-01-16
Yes - I know it does - I want to see them - which was why I told you to post it ;)

---

### Post by WesselPretorius on 2009-01-16
ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:~$

I am working here between my xp pc on this forum and my half working ubuntu one, sorry for the delays.

---

### Post by Elfy on 2009-01-16
it's ok - that is a lower case L not a 1, try again

does the ubuntu livecd not have internet?

---

### Post by WesselPretorius on 2009-01-16
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95709570

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95d895d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95d895d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    7  HPFS/NTFS
ubuntu@ubuntu:~$


Sorry

---

### Post by Elfy on 2009-01-16
None of those are linux drives.

Did you install ubuntu as wubi - that is from inside windows?

If that's the case can you post your windows boot.ini - it should be in the c:\ I think from memory

---

### Post by WesselPretorius on 2009-01-16
no, I have a external which I partitioned, One part is ntsf (200GB), the other (100GB) I istalled linux on and formatted to ext3

---

### Post by Elfy on 2009-01-16
mmm - is everthing plugged in and recognised when you run the fdisk command then?

Because there are no linux partitions showing in the output, they are all NTFS

You have as far as I can tell 

1 x 160Gb
2 x 320Gb

---

### Post by WesselPretorius on 2009-01-16
I have :  160GB - xp main drive
          320GB - xp work drive
          320GB - xp storage drive
an external which is recognized in my Bios because second to my cd/dvd drive it is my boot drive. It is a 320GB partitioned. It seems not to be recognized in the test that I did by your help.

The reason I am doing it the way I have done, is , I am looking into Ubuntu to see if it is worth swithching boots and all, but I have a few work pc's but none to spare for redoing as they are all used. Do you have any Idea on a way to test ubuntu on a machine if the method I use fails (or is obsurd)?

---

### Post by Partyboi2 on 2009-01-16
can you clarify please
> an external which is recognized in my Bios because second to my cd/dvd drive it is my boot drive. It is a 320GB partitioned. It seems not to be recognized in the test that I did by your helpAre you saying you have another external hard drive (320gig)  that you use as well, so you have
160GB - xp main drive
          320GB - xp work drive
          320GB - xp storage drive
and another 320 gig external hardrive?

---

### Post by Elfy on 2009-01-16
Assuming that the external is plugged in can you run this and post the output please.

```
mount
```

At the moment what I'm failing to understand is how you get a grub menu when there are no linux partitions/drives.

When you installed it I assume that the installer found your external then in order for you to have installed, but quite why it's not showing now ?

---

### Post by WesselPretorius on 2009-01-16
I have external 320GB. 200GB is storage for xp, 100GB is ext3 with ubuntu 8.10, I have installed it twice, each time giving grub error 17.

(I have a new report from ubuntu terminal on next page)

---

### Post by WesselPretorius on 2009-01-16
I know it is recognized and connected because it is in my Bios. It will do the check again, maybe I missed something (stupid).

---

### Post by WesselPretorius on 2009-01-16
Here it goes

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95709570

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95d895d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95d895d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb4a612ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       25497   204804621    7  HPFS/NTFS
/dev/sdd2   *       25498       36439    87891615   83  Linux
/dev/sdd3           36440       38913    19872405    5  Extended
/dev/sdd5           36440       38913    19872373+  82  Linux swap / Solaris
ubuntu@ubuntu:~$


I must have missed something, sorry!

---

### Post by Elfy on 2009-01-16
please run these commands

```
sudo mkdir /mnt/tmp
sudo mount -t ext3 /mnt/tmp /dev/sdd2
```

If you get errors and are not pasting - check what you've written

Now run these and paste the outputs please

```
blkid
cat /mnt/tmp/boot/grub/menu.lst
```

---

### Post by WesselPretorius on 2009-01-16
ubuntu@ubuntu:~$ sudo mkdir /mnt/tmp
mkdir: cannot create directory `/mnt/tmp': File exists
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo mount -t ext3 /mnt/tmp /dev/sdd2
mount: /mnt/tmp is not a block device
ubuntu@ubuntu:~$ code]blkid
bash: code]blkid: command not found
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ cat /mnt/tmp/boot/grub/menu.lst
cat: /mnt/tmp/boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$

Have have copied, and found these twice, or did I enter it at the wrong place?

---

### Post by Elfy on 2009-01-16
sorry my mistake

sudo mount -t ext3 /dev/sdd2 /mnt/tmp

---

### Post by WesselPretorius on 2009-01-16
No problem, testing quickly...

ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sdd2 /mnt/tmp
mount: mount point /mnt/tmp does not exist

---

### Post by Elfy on 2009-01-16
run the mkdir command first then - if you rebooted then it would have gone.

---

### Post by WesselPretorius on 2009-01-16
ubuntu@ubuntu:~$ sudo mkdir /mnt/tmp
mkdir: cannot create directory `/mnt/tmp': File exists
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sdd2 /mnt/tmp
mount: /dev/sdd2 already mounted or /mnt/tmp busy
mount: according to mtab, /dev/sdd2 is already mounted on /mnt/tmp
ubuntu@ubuntu:~$ [code]blkid
bash: [code]blkid: command not found
ubuntu@ubuntu:~$ cat /mnt/tmp/boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=45e77bf7-b4ac-446b-aaf2-a1f5738d4406 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=45e77bf7-b4ac-446b-aaf2-a1f5738d4406

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		45e77bf7-b4ac-446b-aaf2-a1f5738d4406
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=45e77bf7-b4ac-446b-aaf2-a1f5738d4406 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		45e77bf7-b4ac-446b-aaf2-a1f5738d4406
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=45e77bf7-b4ac-446b-aaf2-a1f5738d4406 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		45e77bf7-b4ac-446b-aaf2-a1f5738d4406
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
ubuntu@ubuntu:~$ 

v

---

### Post by WesselPretorius on 2009-01-16
Is this what you wanted?

---

### Post by Elfy on 2009-01-16
:) yes - but we need to check something with blkid 

run it again ```
blkid
```

check the number for sdd2 with this 45e77bf7-b4ac-446b-aaf2-a1f5738d4406

they should match exactly.

If they do then try to reinstall grub - information is here

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick) Start

---

### Post by WesselPretorius on 2009-01-16
I have, I get it again, this number is there a few times (uuid		45e77bf7-b4ac-446b-aaf2-a1f5738d4406)

Do you want every thing again?

---

### Post by Elfy on 2009-01-16
Ok - if the number matches then that is right.

When you ran the reistall wiki commands did you get any errors? If you did post them - rerun the commands to get the errors and paste the whole terminal output, but if it said it worked I don't know what is going on tbh.

Maybe try the supergrub disc - download, burn as an iso and boot with it - [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

If that doesn't work then try this - download this
[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055)

and from the terminal run 

```
sudo bash ~/Desktop/boot_info_script*.sh
```

Paste the output of the text doc that is created here - but make sure you put [noparse]```
[/noparse] at the beginning of the paste and [noparse]
```[/noparse] at the end - it is a lot of information and will be too big. 

Perhaps there's information that I need and I'm not asking the right question.

---

### Post by WesselPretorius on 2009-01-16
I did the reinstall grub to which you gave me the link, but now when I want to boot windows it gives error 21. They say it might happen so I am trying to follow the other instructions to get it fixed.

Which is funny because I still get the error 17 when trying to load ubuntu, but I have won myself a error on xp as well.

---

### Post by Elfy on 2009-01-16
Ok I suggest you go no further for the moment.

I don't know whatis going on here - err17 says there's something wrong with the drive, err 21 says the drive doesn't exist.

I don't think that you can actually be using grub - xp isn't even on the menu list, unless you didn't paste the whole list.

Fix the mbr so you can at least boot your xp. Then go back to post 32 - and do the 
> If that doesn't work then try this section.

Once you've posted it I can look at that.

It might be worth doing it the other way and adding ubuntu to the win boot menu.

---

### Post by utnubuuser on 2009-01-16
Hi -- Did you check your CD integrity before installing?

Maybe provide a bit more info, such as which partitioning method you chose, ie. "Use entire disk" or "manual partitioning".

---

### Post by Pumalite on 2009-01-16
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)
If you see Grub; edit the boot until you find the partition.

---

### Post by bapoumba on 2009-01-16
Threads merged.

---

### Post by WesselPretorius on 2009-01-19
I fixed my mbr on my xp drive using a xp install cd. Xp is working fine, so it solved the error 21 issue of xp not booting. Still working on the error 17 issue.

---

