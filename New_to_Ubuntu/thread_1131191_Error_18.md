---
title: "Error 18?"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by Murderuption on 2009-04-20
I've had Ubuntu installed on my laptop (Gateway M-Series) for about a month and a half now.  Today, when I went for a bike ride, I left my laptop powered on and sitting on my couch.  When I came home, it was shut off, which I'm assuming was the result of a dead battery.  I turned it on, it said "Grub loading, please wait. . . Error 18," and it just hangs there and doesn't do anything.  

I googled it and came up with something about the BIOS menu so I went in and changed what I thought had to be changed.  Now, upon restarting, it won't even go past the Gateway screen.  I tried putting in a boot disc for Linux Mint but it still just hangs on the Gateway start-up screen.  

Any help?  I don't want to lose any information!

Thanks a lot! :)

---

### Post by antikristian on 2009-04-21
Boot a livecd if you can, and see if you can access the harddrive. Is the harddrive listed in the bios?

---

### Post by lkraemer on 2009-04-21
I had a couple of the Error 18 messages on my Desktop and it wouldn't
boot.

I read on a post somewhere to change the boot order to anything different
than what it is now, and it will boot.  So, I removed my floppy from
the boot order, and my Desktop booted right up.

Might be worth a try.  It won't cost anything.

I too, would suggest booting a LiveCD, and see if that works.
You might have a hardware problem.  And running memtest86 wouldn't hurt,
if the LiveCD boots.

Worst case, is you pull the harddrive, plug it into a Desktop with a 2.5 to 3.5
adapter and save your files, or use Clonezilla to copy the drive/partition
assuming the drive is still good.

I have a Gateway MT6840, and love it.

SystemRescueCD and Ultimate Boot CD (UBCD) might come in handy.

lkraemer

---

### Post by startling on 2009-04-23
I've been using Feisty on my laptop for well over a year now and very occasionally booting into Vista when forced to. This morning, out of the blue, I have a Grub Error 18 and - typically - I need to do some urgent work on the laptop, so I'd be grateful for help.

I've booted from an 8.10 live CD (which is how I'm posting this) and can mount my hard drive and its partitions. 

Is there a grub file I can edit to make the system work again, or something else? Or is a re-install my only option? If so that would be a real pain because the problem is I have no Vista disk as it was preloaded when I bought the laptop (don't you hate it when they do that?).

Thanks.

---

### Post by antikristian on 2009-04-23
The grub configurationfile is the file /media/<yourdisk>/boot/grub/menu.lst

But editing that blindly probably will not help.
try booting without the livecd and hit the esc kay as soon as grub pops up. If you get a menu, than you can exit the boot options manually, We can get back to that later.

If you get the grub 18 error right away, there is a command we can run from the livecd to restore grub on your MBR.

So restart your computer and hit escape as soon as the bios is finished loading

---

### Post by startling on 2009-04-23
Thanks antikristian.

Is the command you mention:
 grub> setup (hd0)
?

I've been Googling for a solution and found something referencing the above. Would doing something like that remove my Vista and other partitions or would it basically restore grub to a working state?

Thanks again.

---

### Post by antikristian on 2009-04-23
If the MBR is overwritten, and you need to restore it, you can run grub-install /dev/sda (if sda is your primary harddrive)

This would only touch the first 446 bits of your harddrive, which is part of a sector called the master boot record (MBR) 

This sector also contains the partitionsetup of the harddrive, and allthough I have never heard of grub overwriting this sector, you can do a backup by running
```
sudo dd if=/dev/sda of=mbr.img bs=512 count=1
```
before you run the grub command.

After you have run the backup, copy the mbr.img to a usb drive, since copying it to your harddrive would be pretty useless if the partitionsetup disappeard.

In short, no it will not remove or affect vista, it will not destroy your harddrive either, but better safe than sorry, so backup the MBR.

---

### Post by t-mo_ on 2009-04-23
I have a funny bug resulting in the same error message, if I start the computer with a USB stick or USB HD connected. I have to disconnect every USB drive before start. It made me almost reinstalling jaunty....

---

### Post by startling on 2009-04-23
antikristian:

I tried hitting the Esc key but grub went straight to error 18.
I backed up the MBR as you kindly suggested. Then I ran grub-install /dev/sda from a terminal, but it returned the following error:
 
```

Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
```

What should I do now?

Thanks

---

### Post by unutbu on 2009-04-23
startling, please follow [these instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3") to run boot_info_script, and post the RESULTS.txt file here.

---

### Post by startling on 2009-04-23
Thanks unutbu. Here is the results.txt file:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 7.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc7212425

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048    42,424,319    39,350,272   7 HPFS/NTFS
/dev/sda3         118,848,870   156,296,384    37,447,515   5 Extended
/dev/sda5    *    118,848,933   154,641,689    35,792,757  83 Linux
/dev/sda6         154,641,753   156,296,384     1,654,632  82 Linux swap / Solaris
/dev/sda4          42,427,665   104,486,759    62,059,095  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1006 MB, 1006632960 bytes
33 heads, 63 sectors/track, 945 cylinders, total 1966080 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x672e5cdc

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     1,966,079     1,966,017   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="EAE65B12E65ADE7F" LABEL="WinRE" TYPE="ntfs" 
/dev/sda2: UUID="8C1E5DF41E5DD832" LABEL="Vista" TYPE="ntfs" 
/dev/sda4: LABEL="datadisk" UUID="14edb6f7-1332-46cf-922a-22ff341a081b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="7e3a4cb0-7f87-41f9-a051-df146e1eeba4" TYPE="ext3" 
/dev/sda6: UUID="e1c1b04f-24c0-4b16-88cd-de0dbe9016a3" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="USB DISK" UUID="5C92-9CEA" TYPE="vfat" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/USB DISK type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


=========================== sda5/boot/grub/menu.lst: ===========================


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=7e3a4cb0-7f87-41f9-a051-df146e1eeba4 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=e1c1b04f-24c0-4b16-88cd-de0dbe9016a3 none swap sw 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda4 /media/sda4 ext3 errors=remount-ro 0 0

=================== sda5: Location of files loaded by Grub: ===================


  61.4GB: boot/grub/menu.lst
  61.3GB: boot/grub/stage2
  61.3GB: boot/initrd.img-2.6.20-15-generic
  61.4GB: boot/initrd.img-2.6.20-15-generic.bak
  61.5GB: boot/initrd.img-2.6.20-16-generic
  61.4GB: boot/initrd.img-2.6.20-16-generic.bak
  61.5GB: boot/initrd.img-2.6.20-17-generic
  61.4GB: boot/initrd.img-2.6.20-17-generic.bak
  61.4GB: boot/vmlinuz-2.6.20-15-generic
  61.5GB: boot/vmlinuz-2.6.20-16-generic
  61.4GB: boot/vmlinuz-2.6.20-17-generic
  61.5GB: initrd.img
  61.5GB: initrd.img.old
  61.4GB: vmlinuz
  61.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 3c 90 4d 53 57 49 4e  34 2e 31 00 02 20 09 00  |.<.MSWIN4.1.. ..|
00000010  02 00 02 00 00 f8 f0 00  3f 00 40 00 3f 00 00 00  |........?.@.?...|
00000020  c1 ff 1d 00 00 00 29 ea  9c 92 5c 4e 4f 20 4e 41  |......)...\NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 fa 33  |ME    FAT16   .3|
00000040  c9 8e d1 bc fc 7b 16 07  bd 78 00 c5 76 00 1e 56  |.....{...x..v..V|
00000050  16 55 bf 22 05 89 7e 00  89 4e 02 b1 0b fc f3 a4  |.U."..~..N......|
00000060  06 1f bd 00 7c c6 45 fe  0f 8b 46 18 88 45 f9 38  |....|.E...F..E.8|
00000070  4e 24 7d 22 8b c1 99 e8  77 01 72 1a 83 eb 3a 66  |N$}"....w.r...:f|
00000080  a1 1c 7c 66 3b 07 8a 57  fc 75 06 80 ca 02 88 56  |..|f;..W.u.....V|
00000090  02 80 c3 10 73 ed 33 c9  8a 46 10 98 f7 66 16 03  |....s.3..F...f..|
000000a0  46 1c 13 56 1e 03 46 0e  13 d1 8b 76 11 60 89 46  |F..V..F....v.`.F|
000000b0  fc 89 56 fe b8 20 00 f7  e6 8b 5e 0b 03 c3 48 f7  |..V.. ....^...H.|
000000c0  f3 01 46 fc 11 4e fe 61  bf 00 07 e8 23 01 72 39  |..F..N.a....#.r9|
000000d0  38 2d 74 17 60 b1 0b be  d8 7d f3 a6 61 74 39 4e  |8-t.`....}..at9N|
000000e0  74 09 83 c7 20 3b fb 72  e7 eb dd be 7f 7d ac 98  |t... ;.r.....}..|
000000f0  03 f0 ac 84 c0 74 17 3c  ff 74 09 b4 0e bb 07 00  |.....t.<.t......|
00000100  cd 10 eb ee be 82 7d eb  e5 be 80 7d eb e0 98 cd  |......}....}....|
00000110  16 5e 1f 66 8f 04 cd 19  be 81 7d 8b 7d 1a 8d 45  |.^.f......}.}..E|
00000120  fe 8a 4e 0d f7 e1 03 46  fc 13 56 fe b1 04 e8 c1  |..N....F..V.....|
00000130  00 72 d6 ea 00 02 70 00  b4 42 eb 2d 60 66 6a 00  |.r....p..B.-`fj.|
00000140  52 50 06 53 6a 01 6a 10  8b f4 74 ec 91 92 33 d2  |RP.Sj.j...t...3.|
00000150  f7 76 18 91 f7 76 18 42  87 ca f7 76 1a 8a f2 8a  |.v...v.B...v....|
00000160  e8 c0 cc 02 0a cc b8 01  02 8a 56 24 cd 13 8d 64  |..........V$...d|
00000170  10 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |.ar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 80 7e 02  0e e9 40 ff 00 00 55 aa  |.A....~...@...U.|
00000200


=============================== StdErr Messages: ===============================

cat: /media/disk/boot/grub/menu.lst: Input/output error
```

---

### Post by unutbu on 2009-04-23
Boot from the LiveCD

Open a terminal and type
```
sudo sfdisk -A2 /dev/sda

```
This will set the boot flag to /dev/sda2. This is not the main problem, but it corrects a small error (having boot flags set on two partitions is a no-no).

I think the main problem is this error:
```

cat: /media/disk/boot/grub/menu.lst: Input/output error
```

For some reason Linux can not read the file /boot/grub/menu.lst on sda5 (your Linux partition).

Could you post the output of 
```

sudo mount /dev/sda5 /mnt
ls -l /mnt/boot
ls -l /mnt/boot/grub

```

---

### Post by startling on 2009-04-23
Thanks again unutbu. Output of ls -l /mnt/boot:

```
total 50824
-rw-r--r-- 1 root root  414210 2007-04-15 08:07 abi-2.6.20-15-generic
-rw-r--r-- 1 root root  414274 2008-02-12 06:19 abi-2.6.20-16-generic
-rw-r--r-- 1 root root  414274 2008-08-20 17:26 abi-2.6.20-17-generic
-rw-r--r-- 1 root root   83234 2007-04-15 05:33 config-2.6.20-15-generic
-rw-r--r-- 1 root root   83217 2008-02-12 02:45 config-2.6.20-16-generic
-rw-r--r-- 1 root root   83217 2008-08-20 14:43 config-2.6.20-17-generic
drwxr-xr-x 2 root root    4096 2008-08-26 10:07 grub
-rw-r--r-- 1 root root 7161554 2007-06-24 17:12 initrd.img-2.6.20-15-generic
-rw-r--r-- 1 root root 6842512 2007-04-15 11:56 initrd.img-2.6.20-15-generic.bak
-rw-r--r-- 1 root root 7151763 2008-02-13 07:22 initrd.img-2.6.20-16-generic
-rw-r--r-- 1 root root 7151753 2008-02-05 07:23 initrd.img-2.6.20-16-generic.bak
-rw-r--r-- 1 root root 7150966 2008-08-26 10:07 initrd.img-2.6.20-17-generic
-rw-r--r-- 1 root root 7151446 2008-07-16 09:31 initrd.img-2.6.20-17-generic.bak
-rw-r--r-- 1 root root   94600 2006-10-20 11:44 memtest86+.bin
-rw-r--r-- 1 root root  806942 2007-04-15 08:08 System.map-2.6.20-15-generic
-rw-r--r-- 1 root root  807071 2008-02-12 06:20 System.map-2.6.20-16-generic
-rw-r--r-- 1 root root  807097 2008-08-20 17:28 System.map-2.6.20-17-generic
-rw-r--r-- 1 root root 1745100 2007-04-15 08:07 vmlinuz-2.6.20-15-generic
-rw-r--r-- 1 root root 1747532 2008-02-12 06:19 vmlinuz-2.6.20-16-generic
-rw-r--r-- 1 root root 1747692 2008-08-20 17:26 vmlinuz-2.6.20-17-generic

```

Output of ls -l /mnt/boot/grub:

```
total 212
-rw-r--r-- 1 root root    197 2007-06-24 17:12 default
-rw-r--r-- 1 root root     30 2007-06-24 17:12 device.map
-rw-r--r-- 1 root root   8660 2007-06-24 17:12 e2fs_stage1_5
-rw-r--r-- 1 root root   8452 2007-06-24 17:12 fat_stage1_5
-rw-r--r-- 1 root root     15 2007-06-24 17:12 installed-version
-rw-r--r-- 1 root root   9152 2007-06-24 17:12 jfs_stage1_5
-rw-r--r-- 1 root root   5336 2008-08-26 10:07 menu.lst
-rw-r--r-- 1 root root   5336 2008-08-26 10:07 menu.lst~
-rw-r--r-- 1 root root   7860 2007-06-24 17:12 minix_stage1_5
-rw-r--r-- 1 root root  10132 2007-06-24 17:12 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2007-06-24 17:12 stage1
-rw-r--r-- 1 root root 110132 2007-06-24 17:12 stage2
-rw-r--r-- 1 root root   9980 2007-06-24 17:12 xfs_stage1_5
```

---

### Post by unutbu on 2009-04-23
Please post 
```

cat /mnt/boot/grub/menu.lst
```

---

### Post by startling on 2009-04-23
Ouput:
```
cat: /mnt/boot/grub/menu.lst: Input/output error
```

So I tried opening the file in gedit but it could not, and returned the error:
Could not open the file /mnt/boot/grub/menu.lst.

Is my menu.lst somehow corrupt?

Thanks again.

---

### Post by unutbu on 2009-04-23
Yes, it appears there is some filesystem corruption. e2fsck is the tool to use to fix ext2/ext3 filesystems.

Let's try this:
```
sudo umount /dev/sda5
sudo e2fsck -C0 -pfv /dev/sda5
sudo mount /dev/sda5 /mnt
cat /mnt/boot/grub/menu.lst
```

Please post the output if it isn't too long. If it is very long, please post the beginning and ending parts of the e2fsck output.

---

### Post by startling on 2009-04-23
I didn't get as far as mounting sda5 again, because e2fsck returned this:

```
/dev/sda5: Superblock has an invalid ext3 journal (inode 8).
CLEARED.
*** ext3 journal has been deleted - filesystem is now ext2 only ***

/dev/sda5: Journal inode is not in use, but contains data.  CLEARED.
Error reading block 33809 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  

/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)

```

I don't know how to run fsck manually as suggested.

---

### Post by startling on 2009-04-23
Update: I ran sudo fsck /dev/sda5 and it returned the following:
```

Pass 1: Checking inodes, blocks, and sizes
Error reading block 33809 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 33810 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes
```

And so on for the next 3 blocks so I assumed this might go on for a while and aborted. Does this mean my disk is broken?

---

### Post by unutbu on 2009-04-23
startling, your disk is not broken. The filesystem inside your sda5 partition has some problems, however. 

Proceeding with the fsck command is the usual way to recover from filesystem corruption.
However, using fsck can also lead to data loss. Files that were open or not yet written to disk when the machine shutdown could be lost.

If you don't think there is anything super-important that was open or not yet written to disk when the machine shutdown (causing the current problem), then run

```
sudo umount /dev/sda5
sudo e2fsck -fvy /dev/sda5
```

This will run fsck, answering "yes" to all questions. 

If you want to make sure you lose as little data as possible, then you'll need to clone your partition using a tool like ddrescue ([http://www.gnu.org/software/ddrescue/ddrescue.html](http://www.gnu.org/software/ddrescue/ddrescue.html)) or partimage ([http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)). Once you have the partition backed up on another drive, then you would use recovery tools like PhotoRec, foremost, or scalpel to search and recover data. (See [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)).

That can be a lot of work. 

In most cases, especially if you have backups of your data, I'd say the normal, reasonable thing to do is just run
```

sudo umount /dev/sda5
sudo e2fsck -fvy /dev/sda5
```

but please be aware it can lead to some data loss.

---

### Post by startling on 2009-04-23
Thanks unutbu - I have to say this is absolutely fantastic support. 

I am running fsck as you suggest and there seems to be a lot of errors so I suppose it will take a while and I will lose a lot of data - fortunately I have backups of the important stuff!

I assume that my menu.lst is part of the data being lost, so do I need to recreate it? If that's the case I have no idea how to do that though!

Thanks again.

---

### Post by unutbu on 2009-04-23
When e2fsck is done, try seeing if menu.lst is readable:

```
sudo mount /dev/sda5 /mnt
cat /mnt/boot/grub/menu.lst
```

If it is, try rebooting. If it is not readable, run

```
sudo mount /dev/sda5  /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt       
grub-install --recheck /dev/sda
update-grub

```
This sequence of commands should reinstall GRUB and regenerate /boot/grub/menu.lst.

---

### Post by startling on 2009-04-24
I'm concerned that my disk is faulty. The fsck has found a lot of errors and is still running after more than two hours. Is it normal to take this long?

---

### Post by unutbu on 2009-04-24
Usually fsck does not take this long. I don't think it necessarily means your disk drive is faulty, but it could mean there will be a lot of data loss.  :(

Superblocks are the ext3 equivalent of FAT (file allocation tables). It is the superblock that e2fsck manipulates. If the first superblock was damaged badly, then e2fsck might take a long time. Maybe, one of the backup superblocks is in better shape. 

How about try this:

Ctrl-C to stop e2fsck.

Then type
```

sudo dumpe2fs /dev/sda5 | awk /superblock/{'print $4'}
```

You should see something like

```
dumpe2fs 1.41.3 (12-Oct-2008)
0,
32768,
98304,
163840,
229376,
294912,
819200,
884736,
1605632,
2654208,
4096000,
```

These are the locations of backup superblocks. Choose a number > 1 from the list (e.g. 32768). 


Then type:```

sudo e2fsck -b 32768 -fy -C0 /dev/sda5
```

This will run e2fsck using the backup superblock located at 32768.
It should also report a progress bar, instead of the verbose messages.

If the original e2fsck command has finished by the time you read this, and if you find there are a lot of missing files, then you can still try 
```

sudo e2fsck -b 32768 -fy -C0 /dev/sda5
```
because e2fsck only manipulates the superblock. It does not touch the underlying data in the partition.

---

### Post by startling on 2009-04-25
Thanks again unutbu, but as there were so many errors and e2fsck continued running for so long I assumed the disk was faulty, so before I saw your reply I bought a new disk and installed 8.10 on that - it's one way of upgrading I suppose! 

Your replies have been most helpful with clear, easy to follow instructions.

---

### Post by unutbu on 2009-04-25
That's fine, startling. I'm glad to hear you are back up and running, by any method that works. Good luck; I hope you are able to recover your data.

---

