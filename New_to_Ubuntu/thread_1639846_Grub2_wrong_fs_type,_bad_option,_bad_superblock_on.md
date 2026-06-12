---
title: "Grub2: wrong fs type, bad option, bad superblock on /dev/sda6"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by abybaddi on 2010-12-07
After I formatted my xp and tried to reinstall the grub...
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x30123011

Device Boot Start End Blocks Id System
/dev/sda1 2 2550 20473985 f W95 Ext'd (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2 * 2551 19456 135797413+ 7 HPFS/NTFS
/dev/sda5 2 1345 10795618 7 HPFS/NTFS
/dev/sda6 1346 2493 9212928 83 Linux
/dev/sda7 2493 2550 460800 82 Linux swap / Solaris

Disk /dev/sdb: 4063 MB, 4063232000 bytes
125 heads, 62 sectors/track, 1024 cylinders
Units = cylinders of 7750 * 512 = 3968000 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007e048

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 1024 3967969 c W95 FAT32 (LBA)

ubuntu@ubuntu:~$ sudo mkdir /media/sda6
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /media/sda6
mount: wrong fs type, bad option, bad superblock on /dev/sda6,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

ubuntu@ubuntu:~$


I got such diabolical error... please help me I don't want to lose my files on that system...

---

### Post by Paqman on 2010-12-07
If you just want to mount the partition temporarily you don't need to use the command line, you can just browse and click on it. It'll get mounted in /media by default.

If you want something permanent (and which automatically mounts itself at boot) then there's some good instructions on [Psychocats](http://www.psychocats.net/ubuntu/mountlinux).

---

### Post by Rubi1200 on 2010-12-07
Run the boot info script linked at the bottom of my post (instructions included).

Post the results back here please.

Thanks.

---

### Post by abybaddi on 2010-12-07
Here we go..

>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,126    40,964,095    40,947,970   f W95 Ext d (LBA)
/dev/sda5              16,189    21,607,424    21,591,236   7 HPFS/NTFS
/dev/sda6          21,614,592    40,040,447    18,425,856  83 Linux
/dev/sda7          40,042,496    40,964,095       921,600  82 Linux swap / Solaris
/dev/sda2    *     40,965,813   312,560,639   271,594,827   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4063 MB, 4063232000 bytes
125 heads, 62 sectors/track, 1024 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     7,935,999     7,935,938   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       cf061a67-a398-47b8-8f20-d24171c78437   ext3                                     
/dev/sda1: PTTYPE="dos" 
/dev/sda2        4CFF6C2522EEA480                       ntfs       Data                          
/dev/sda5        445899BF5899B062                       ntfs                                     
/dev/sda6        49724adf-07f4-4190-9fb7-986bda5c3cc4   ext4                                     
/dev/sda7        47161ba1-17c6-4d4e-8032-262907822e86   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6C26-9974                              vfat       4GiB                          
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  0a 13 17 04 14 0d 2a 40  36 03 30 27 00 db 1d 0d  |......*@6.0'....|
00000010  30 3d da 14 43 24 20 1d  03 43 1a 00 0a 09 06 03  |0=..C$ ..C......|
00000020  05 40 13 10 33 17 2a 03  2d 1a 39 40 14 36 1a 40  |.@..3.*.-.9@.6.@|
00000030  10 04 2d 1a 43 10 d4 c4  fc c4 12 39 39 12 39 11  |..-.C......99.9.|
00000040  12 17 39 12 39 11 17 39  11 12 17 39 31 00 10 c4  |..9.9..9...91...|
00000050  fc c4 d4 3c e4 39 11 17  39 11 12 17 39 11 12 39  |...<.9..9...9..9|
00000060  11 12 17 39 12 39 30 01  32 16 17 16 16 17 06 06  |...9.90.2.......|
00000070  07 07 22 26 23 22 06 23  02 02 15 07 26 26 27 36  |.."&#".#....&&'6|
00000080  36 35 34 26 35 22 26 27  34 27 26 35 34 36 37 32  |654&5"&'4'&54672|
00000090  36 37 26 02 27 36 36 33  32 16 17 16 16 17 36 36  |67&.'6632.....66|
000000a0  37 36 37 36 33 32 16 17  06 02 01 54 25 49 23 03  |767632.....T%I#.|
000000b0  03 01 01 03 03 1a 10 2f  07 06 28 0f 06 05 56 10  |......./..(...V.|
000000c0  28 19 08 08 02 25 4a 27  02 0a 0a 0d 27 43 1d 1c  |(....%J'....'C..|
000000d0  4d 41 11 2e 1f 04 16 07  29 44 1a 21 41 25 07 0d  |MA......)D.!A%..|
000000e0  16 05 10 2b 25 1c 68 02  d7 06 06 0b 13 09 0c 1b  |...+%.h.........|
000000f0  0d 0e 02 02 fe e2 fe f7  4f 0d 0b 0e 04 86 f6 6f  |........O......o|
00000100  16 53 14 06 07 01 05 1a  0b 07 18 16 04 04 71 01  |.S............q.|
00000110  0e cd 1d 1c 03 01 6a e3  7a a4 dd 4e 01 01 02 0b  |......j.z..N....|
00000120  0f 37 fe ab 00 01 ff 91  fe 56 04 1b 04 2d 00 26  |.7.......V...-.&|
00000130  00 43 40 29 17 27 1a 16  13 0d 0a 01 05 1d 23 00  |.C@).'........#.|
00000140  07 df 20 1a de 24 e0 0b  00 dc 27 26 24 23 1d 17  |.. ..$....'&$#..|
00000150  16 10 0d 0b 0a 04 01 00  0d 27 0c 25 27 10 d4 c4  |.........'.%'...|
00000160  11 17 39 31 00 10 e4 32  ec f4 3c ec 11 39 39 17  |..91...2..<..99.|
00000170  39 11 12 39 30 01 03 06  06 15 14 16 33 32 36 37  |9..90.......3267|
00000180  13 33 03 06 06 15 14 16  33 32 36 37 07 06 06 23  |.3......3267...#|
00000190  22 26 27 06 06 23 22 26  27 03 23 01 01 6a 7e 08  |"&'..#"&'.#..j~.|
000001a0  07 72 67 7d a6 2d 79 9c  a2 0c 0b 25 23 09 11 09  |.rg}.-y....%#...|
000001b0  1b 15 2e 19 46 45 06 29  98 60 57 83 2c 71 00 01  |....FE.).`W.,q..|
000001c0  3e 01 07 fe ff ff 3f 00  00 00 c4 74 49 01 00 5f  |>.....?....tI.._|
000001d0  fe ff 05 66 ea ff a1 8c  49 01 61 2c 19 01 00 00  |...f....I.a,....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



Look again the error in the result file:
> wrong fs type, bad option, bad superblock on /dev/sda6,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

what's the unidentified boot loader??

it's driving me nuts!!!

---

### Post by Paqman on 2010-12-07
What instructions did you follow to reinstall Grub?

---

### Post by abybaddi on 2010-12-07
A month ago I had formatted my xp due to virus problems and I had used this guide:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Rubi1200 on 2010-12-07
I hope Paqman will forgive me for jumping in (again).

> what's the unidentified boot loader??
I have seen this before with boot info results. For some reason (someone else may have a real explanation) it appears to sometimes misidentify extended partitions as boot sectors. Nothing to worry about in your case though.

The file errors are, however, of concern.

I suggest you boot from a LiveCD and run the following file-system checks:

```
sudo e2fsck -C0 -p -f -v /dev/sda6
```

If there are errors, run this:

```
sudo e2fsck -f -y -v /dev/sda6
```
When finished, reboot without the CD and let us know if it helped.

---

### Post by abybaddi on 2010-12-08
This is what I did:
> mint@mint ~ $ sudo e2fsck -C0 -p -f -v /dev/sda6
/dev/sda6: recovering journal
Error reading block 1082502 (Attempt to read block from filesystem resulted in short read).  

/dev/sda6: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
mint@mint ~ $ sudo e2fsck -f -y -v /dev/sda6
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda6: recovering journal
Error reading block 1082502 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Clearing orphaned inode 2387 (uid=1001, gid=1001, mode=0100644, size=32768)
Clearing orphaned inode 2231 (uid=1001, gid=1001, mode=0100600, size=272)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda6: ***** FILE SYSTEM WAS MODIFIED *****

  307259 inodes used (53.35%)
     262 non-contiguous files (0.1%)
     343 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 229627/136/1
 2027173 blocks used (88.01%)
       0 bad blocks
       1 large file

  197545 regular files
   24366 directories
      60 character device files
      26 block device files
       0 fifos
     485 links
   85200 symbolic links (77346 fast symbolic links)
      53 sockets
--------
  307735 files
mint@mint ~ $ 


---

### Post by abybaddi on 2010-12-08
First I booted into my newest kernel. I played the login sound but showed no usernames to select, but just the wallpaper that is default into the ubuntu.

Then I selected my old kerel, showed the boot screenand then everything went black. So I tried the recovery option and I got the message in the second attachment.

---

### Post by Rubi1200 on 2010-12-08
Hi abybaddi,
a quick search does not really reveal any useful information. Apparently, these errors might, and I stress might, be caused by hard-drive failure, hardware failures, a kernel bug etc.

One thing I suggest you try is to check that all your power cables are connected properly as well as the SATA/IDE controllers.

I will keep looking to try and find something that can help.

---

### Post by abybaddi on 2010-12-09
> **Rubi1200 said:**
> 
One thing I suggest you try is to check that all your power cables are connected properly as well as the SATA/IDE controllers.

I will keep looking to try and find something that can help.
Thank you for that, buddy.:)
I've disconnected and connected them many times but futile.

Is there a way to chkdsk via the linuxmint 10.04?:-?

---

### Post by Rubi1200 on 2010-12-09
Sometimes the results of the script can be misleading.

Let's try and purge then reinstall GRUB using the chroot method.

Use this fantastic guide by drs305:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Change the partition number to sda6 for the chroot method.

---

