---
title: "vista appears unallocated and will not boot"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by weruder on 2008-12-28
Hi, 
I have been running Ubuntu live for about two weeks now and decided to come here for help. While I was trying to install Ubuntu to an external HD, my vista (on a separate hard drive) became inoperable. When I took a look at it in GParted, it said it was unallocated. However, the operating system still appears under Ubuntu and all the files are intact. I considered backing up the files and going back to factory settings but: 1) I don't know if it will reset when vista recovery disc cannot find the hard drive and 2) I'm afraid of messing things up even more. I haven't tried booting into it from virtual box or anything of the sort, but I have a feeling it's a filesystem error so it may not work anyway. I'll see if I can get into it tomorrow.
Thanks

---

### Post by caljohnsmith on 2008-12-28
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Windows problem might be.

---

### Post by weruder on 2008-12-29
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 98304.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 21069824.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       96389       48163+  de  Dell Utility
/dev/sda2           98304    21077279    10489488    7  HPFS/NTFS
/dev/sda3   *    21069824   625153409   302041793    7  HPFS/NTFS

sfdisk -V /dev/sda:

Warning: partitions 2 and 3 overlap

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0C1C" TYPE="vfat" 
/dev/sda2: UUID="7C447E13447DD07E" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="FA4A81AB4A8164EB" LABEL="OS" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

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
/dev/sda3 on /media/OS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

================================== sda3/Boot: ==================================

total 764
drwxrwxrwx 1 root root   4096 2008-08-24 20:37 .
drwxrwxrwx 1 root root  12288 2008-12-29 01:50 ..
-rwxrwxrwx 1 root root  28672 2008-12-27 22:50 BCD
-rwxrwxrwx 1 root root 262144 2008-12-27 22:50 BCD.LOG
-rwxrwxrwx 2 root root      0 2006-11-10 13:22 BCD.LOG1
-rwxrwxrwx 2 root root      0 2006-11-10 13:22 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2006-11-10 13:22 bootstat.dat
drwxrwxrwx 1 root root      0 2008-08-24 20:37 cs-CZ
drwxrwxrwx 1 root root      0 2008-08-24 20:37 da-DK
drwxrwxrwx 1 root root      0 2008-08-24 20:37 de-DE
drwxrwxrwx 1 root root      0 2008-08-24 20:37 el-GR
drwxrwxrwx 1 root root      0 2008-08-24 20:37 en-US
drwxrwxrwx 1 root root      0 2008-08-24 20:37 es-ES
drwxrwxrwx 1 root root      0 2008-08-24 20:37 fi-FI
drwxrwxrwx 1 root root      0 2008-08-24 20:37 Fonts
drwxrwxrwx 1 root root      0 2008-08-24 20:37 fr-FR
drwxrwxrwx 1 root root      0 2008-08-24 20:37 hu-HU
drwxrwxrwx 1 root root      0 2008-08-24 20:37 it-IT
drwxrwxrwx 1 root root      0 2008-08-24 20:37 ja-JP
drwxrwxrwx 1 root root      0 2008-08-24 20:37 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-19 07:43 memtest.exe
drwxrwxrwx 1 root root      0 2008-08-24 20:37 nb-NO
drwxrwxrwx 1 root root      0 2008-08-24 20:37 nl-NL
drwxrwxrwx 1 root root      0 2008-08-24 20:37 pl-PL
drwxrwxrwx 1 root root      0 2008-08-24 20:37 pt-BR
drwxrwxrwx 1 root root      0 2008-08-24 20:37 pt-PT
drwxrwxrwx 1 root root      0 2008-08-24 20:37 ru-RU
drwxrwxrwx 1 root root      0 2008-08-24 20:37 sv-SE
drwxrwxrwx 1 root root      0 2008-08-24 20:37 tr-TR
drwxrwxrwx 1 root root      0 2008-08-24 20:37 zh-CN
drwxrwxrwx 1 root root      0 2008-08-24 20:37 zh-HK
drwxrwxrwx 1 root root      0 2008-08-24 20:37 zh-TW

=============================== StdErr Messages: ===============================

Unknown BootLoader  on /dev/sda1

00000000  eb 54 90 44 65 6c 6c 20  38 2e 30 00 02 04 01 00  |.T.Dell 8.0.....|
00000010  02 00 02 00 00 f8 5e 00  3f 00 ff 00 3f 00 00 00  |......^.?...?...|
00000020  47 78 01 00 80 00 29 1c  0c d7 07 44 65 6c 6c 55  |Gx....)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 10 00  |tilityFAT16   ..|
00000040  01 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 33 c0  8e d0 bc 00 07 fc b9 80  |......3.........|
00000060  00 8e d8 be 00 7c b8 00  20 8e c0 33 ff f3 66 a5  |.....|.. ..3..f.|
00000070  ea 75 00 00 20 8e d8 be  cc 01 b8 01 02 b9 01 00  |.u.. ...........|
00000080  b6 00 8a 16 24 00 bb 00  02 cd 13 0f 82 0c 01 80  |....$...........|
00000090  3e c2 03 06 74 0e c6 06  c2 03 06 b8 01 03 cd 13  |>...t...........|
000000a0  0f 82 f7 00 66 0f b7 06  0e 00 66 03 06 1c 00 66  |....f.....f....f|
000000b0  0f b7 0e 16 00 66 d1 e1  66 03 c1 66 a3 46 00 66  |.....f..f..f.F.f|
000000c0  0f b7 0e 11 00 89 0e 52  00 83 c1 0f c1 e9 04 88  |.......R........|
000000d0  0e 40 00 66 03 c1 66 a3  4e 00 b8 00 30 a3 44 00  |.@.f..f.N...0.D.|
000000e0  8e c0 e8 d4 00 33 db b9  0b 00 be e1 01 8b fb f3  |.....3..........|
000000f0  a6 74 0f 83 c3 20 ff 0e  52 00 75 eb be d7 01 e9  |.t... ..R.u.....|
00000100  99 00 26 8b 47 1a a3 54  00 a1 16 00 a3 52 00 66  |..&.G..T.....R.f|
00000110  0f b7 06 0e 00 66 03 06  1c 00 66 a3 46 00 a1 52  |.....f....f.F..R|
00000120  00 3d 40 00 76 02 b0 40  a2 40 00 e8 8b 00 66 0f  |.=@.v..@.@....f.|
00000130  b6 06 40 00 66 01 06 46  00 29 06 52 00 74 09 c1  |..@.f..F.).R.t..|
00000140  e0 05 01 06 44 00 eb d6  c7 06 44 00 70 00 a0 0d  |....D.....D.p...|
00000150  00 a2 40 00 66 0f b7 06  54 00 66 83 e8 02 66 0f  |..@.f...T.f...f.|
00000160  b6 0e 0d 00 66 f7 e1 66  03 06 4e 00 66 a3 46 00  |....f..f..N.f.F.|
00000170  e8 46 00 8b 36 54 00 b8  00 30 d1 e6 73 03 05 00  |.F..6T...0..s...|
00000180  10 8e c0 26 ad 3d f8 ff  73 16 a3 54 00 0f b6 06  |...&.=..s..T....|
00000190  0d 00 c1 e0 09 01 06 42  00 eb b9 e8 0d 00 eb fe  |.......B........|
000001a0  8a 16 24 00 33 ed ea 00  00 70 00 b4 0e ac bb 07  |..$.3....p......|
000001b0  00 cd 10 80 3c 00 75 f3  c3 b4 42 8a 16 24 00 be  |....<.u...B..$..|
000001c0  3e 00 cd 13 72 01 c3 be  cc 01 eb cf 44 69 73 6b  |>...r.......Disk|
000001d0  20 65 72 72 6f 72 00 4e  6f 20 6c 6f 61 64 65 72  | error.No loader|
000001e0  00 44 45 4c 4c 42 49 4f  20 42 49 4e 00 00 00 00  |.DELLBIO BIN....|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

No errors were reported.
```

Apparently nothing is wrong with the HD itself, maybe it's the bootloader? Sorry, i'm relatively new to this. I also noticed that sda2 and sda3 overlap, but does that have to do with anything? I'll try booting from GRUB and see if it works.

---

### Post by caljohnsmith on 2008-12-29
Unfortunately it looks like you have a corrupt partition table on the Vista drive, and that is most likely what is causing your current problems; as the error shows from the script results, partitions sda2 and sda3 overlap when they shouldn't. Did you recently do any changes to the partitions on that drive? Since your Vista install on sda3 is mountable and readable at least, I would recommend backing up all your important files first, and then you can use "testdisk" to repair your HDD's partition table. If you have an Intrepid Live CD, that would be ideal, because that CD will download testdisk version 6.9; if you use a previous version of testdisk, you won't be able to get a directory listing of your NTFS partitions that you want to recover, and it will be more difficult to make sure we recover the correct partitions. 

From the Intrepid Live CD, first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", "quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Once it is done and displays a list of partitions, use the up/down arrow keys to select each partition, and the press "p" to get a directory listing; please post the output of the screen that has the deep search results, and also let me know which partitions in the list give you a directory listing. We can work from there if you want.

---

### Post by weruder on 2008-12-29
```
Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1     5 254 63      96327 [DellUtility]
D FAT32 LBA                6   0  1  4183 254 63   67119570 [NO NAME]
D HPFS - NTFS              6  30 25  1311 136 41   20971520 [RECOVERY]
D HPFS - NTFS           1311 136 42 38913  37 36  604069888 [OS]









```
They all give a directory listing. Correct me if i'm wrong but are the last three partitions shown as being deleted? It would be great if you could tell me what to do from here, I don't want to do anything unnecessary. Also, I had done some partitioning earlier on my external HD. That may have been when it got corrupted.

---

### Post by caljohnsmith on 2008-12-29
> **weruder said:**
> ```
Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]P[/COLOR] FAT16 >32M               0   1  1     5 254 63      96327 [DellUtility]
[COLOR="Red"]D[/COLOR] FAT32 LBA                6   0  1  4183 254 63   67119570 [NO NAME]
[COLOR="Red"]P[/COLOR] HPFS - NTFS              6  30 25  1311 136 41   20971520 [RECOVERY]
[COLOR="Red"]*[/COLOR] HPFS - NTFS           1311 136 42 38913  37 36  604069888 [OS]

```

OK, how about using your up/down arrow keys to select each partition, and then use the right/left arrow keys to mark each partition as I've highlighted in red above. Once you are sure you have the all partitions marked exactly as shown above, press enter to get to the next screen, and choose the option to write the new partition table. Then reboot, see if you can boot into Vista OK, and if not, go ahead and boot your Live CD and post the output of:
```
sudo fdisk -l
sudo sfdisk -luS
sudo sfdisk -V 
```
And we can work from there. Most likely you should be able to boot into Vista just fine though.

---

### Post by weruder on 2008-12-29
It works! Thanks for the help and i'll be sure to take better precautions when partitioning.

---

### Post by caljohnsmith on 2008-12-29
Glad that worked OK; just as a small side note though, I would recommend using Vista's Disk Management if you want to do any partition changes to that drive, because otherwise you can run into problems if you use a different partition editor. Vista is really finicky because it maintains its own partition outside of the main partition table stored in the HDD's MBR (Master Boot Record), so changing partitions with something other than Vista's own tools can cause problems with Vista. It's not absolutely necessary, because even if you use some other tools to repartition the drive, and if Vista breaks, you can fix Vista with the right tools. Anyway, good luck and let me know if you run into any more problems with it. :)

---

