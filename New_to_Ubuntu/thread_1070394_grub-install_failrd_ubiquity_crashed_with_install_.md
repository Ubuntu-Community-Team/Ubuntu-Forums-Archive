---
title: "grub-install failrd: ubiquity crashed with install step error"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by backfour94 on 2009-02-15
Hi, put some of this on a differnet thread but I think that the title was limiting responses.

I have Windows XP Home imstalled.

I want to move to a dual boot with Ubuntu having succesfully run the 8.10 live disc.  I had problems with the partitioner in the Ubuntu install no matter how many times I defrag and chkdsk.

So I decided to have a go with Fedora which partitioned the drive fine and installed fine.  But I want to use Ubuntu.

So I got a new download of 8.10 and burnt a new CD.  After some great help for this forum the install process ran through almost to the end but then fails with:

Executing 'grub-install (hd0)' failed. This is a fatal effor.

Then:

Sorry the program "ubiquity" closed unexpectedly.  If you were not doing ....... you can report this problem.

Which I did and launchpad pointed me to a thread around bug 260001.  Which is far too technical for me to understand.  

So now I need to know what to do next.  I've tried booting from GRUB (which still has the fedora look and feel but that fails.  I may have the Kernel command wrong but I've tried various versions.

One option is to sort out what it wrong.

Second, it seems, is to boot from a floppy but that would need the Kernel command to be correct.

Third, to start over again, i.e. remove the boot and ubunto partitions going back to XP and start the install from stratch.

All help welcomed, thanks.

---

### Post by caljohnsmith on 2009-02-15
How about trying to install Ubuntu again, but this time when you go through the installer and get to the final stage of the installation setup dialogues, click the "Advanced" button, and specify to have Grub installed to "/dev/sda" and let me know if that works. Often that circumvents the Grub error you are getting during installation, so hopefully it will work in your case. Let me know how it goes.

---

### Post by backfour94 on 2009-02-15
Thanks just to check;

Should it be /dev/sda or /dev/sda2?

It's just that my disk has /dev/sda1 (XP) /dev/sda2 (boot) /dev/sda3 ubuntu.

---

### Post by caljohnsmith on 2009-02-15
> **backfour94 said:**
> Thanks just to check;

Should it be /dev/sda or /dev/sda2?

It's just that my disk has /dev/sda1 (XP) /dev/sda2 (boot) /dev/sda3 ubuntu.
You would want to use "/dev/sda" so that Grub gets installed to the MBR (Master Boot Record) in order to allow you to dual boot. :)

---

### Post by backfour94 on 2009-02-15
OK, I've kicked it off so let's see.

Thanks

---

### Post by backfour94 on 2009-02-15
Nope, same thinh I'm afraid only this time it said:

Unable ro install GRUB in /dev/sda

and

Executing 'grub-install /dev/sda' failed.  This is a fatal error.

---

### Post by caljohnsmith on 2009-02-15
OK, one more way I know of to get around the "fatal Grub install error" bug is to format your Ubuntu partition to use ext2 instead of ext3. If that works and you can install Ubuntu successfully, it is really easy to "upgrade" your Ubuntu partition to ext3 afterwards. How about giving that a shot and let me know if it works.

---

### Post by backfour94 on 2009-02-15
Nope, same thing.  I specified GRUB in /dev/sda and ext2 for the ubuntu partition and got exactly the same result.

Do you think I should be able to boot from the GRUB prompt or has the install not far enough?

---

### Post by caljohnsmith on 2009-02-15
If Grub is the only thing that was not installed, it is possible to manually install Grub afterwards. To see if that might be your case, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and give us an idea if installing Grub might be all it takes to complete your installation.

---

### Post by backfour94 on 2009-02-15
Got this:

bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory

---

### Post by backfour94 on 2009-02-15
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks at sector 41076344 
    on boot drive #1 for the stage2 file. A stage2 file is at this location on 
    /dev/sda. Stage2 looks on partition #2 for /grub/grub.conf.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  The info in boot sector on the starting sector of the 
                       MFT is wrong. The info in the boot sector on the 
                       starting sector of the MFT Mirror is wrong. According 
                       to the info in the boot sector, sda1 has 39062499 
                       sectors, but according to the info from fdisk, it has 
                       40960000 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sda3: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x69086908

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,960,062    40,960,000   7 HPFS/NTFS
/dev/sda2          40,965,750    41,367,374       401,625  83 Linux
/dev/sda3          41,367,375    78,156,224    36,788,850  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="680C59410C590B86" TYPE="ntfs" 
/dev/sda2: LABEL="/boot" UUID="bc33112d-e28a-4dbc-9e87-38748c35b127" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="7988d336-8d8a-4d7b-a58f-3ef56fc3d1f5" TYPE="ext2" 
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
/dev/sda3 on /target type ext2 (rw,relatime,errors=remount-ro)
/proc on /target/proc type none (rw,bind)
/dev on /target/dev type none (rw,bind)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


============================= sda2/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,1)
#          kernel /vmlinuz-version ro root=/dev/VolGroup00/LogVol00
#          initrd /initrd-version.img
#boot=/dev/sda
default=1
timeout=5
splashimage=(hd0,1)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.27.5-117.fc10.i686)
	root (hd0,1)
	kernel /vmlinuz-2.6.27.5-117.fc10.i686 ro root=UUID=bea16924-5919-4266-90c7-5cc75e783466 rhgb quiet
	initrd /initrd-2.6.27.5-117.fc10.i686.img
title Other
	rootnoverify (hd0,0)
	chainloader +1

=================== sda2: Location of files loaded by Grub: ===================


  21.0GB: grub/grub.conf
  21.0GB: grub/menu.lst
  21.0GB: grub/stage2
  20.9GB: initrd-2.6.27.5-117.fc10.i686.img
  20.9GB: vmlinuz-2.6.27.5-117.fc10.i686

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=7988d336-8d8a-4d7b-a58f-3ef56fc3d1f5 /               ext2    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  27.5GB: boot/grub/stage2
  27.5GB: boot/initrd.img-2.6.27-7-generic
  27.5GB: boot/vmlinuz-2.6.27-7-generic
  27.5GB: initrd.img
  27.5GB: vmlinuz

=========================== Unknown MBRs/Boot Sectors/etc =======================

MFT Sector of sda1

00000000  46 49 4c 45 30 00 03 00  14 53 2f 8c 36 00 00 00  |FILE0....S/.6...|
00000010  01 00 01 00 38 00 01 00  38 03 00 00 00 04 00 00  |....8...8.......|
00000020  00 00 00 00 00 00 00 00  23 00 00 00 00 00 00 00  |........#.......|
00000030  e6 20 00 00 00 00 00 00  10 00 00 00 60 00 00 00  |. ..........`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  f0 58 ae 45 8f 79 c1 01  f0 58 ae 45 8f 79 c1 01  |.X.E.y...X.E.y..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  20 00 00 00 78 01 00 00  |........ ...x...|
000000a0  00 00 18 00 00 00 22 00  60 01 00 00 18 00 00 00  |......".`.......|
000000b0  10 00 00 00 20 00 00 1a  00 00 00 00 00 00 00 00  |.... ...........|
000000c0  00 00 00 00 00 00 01 00  00 00 00 00 00 00 24 00  |..............$.|
000000d0  30 00 00 00 20 00 00 1a  00 00 00 00 00 00 00 00  |0... ...........|
000000e0  00 00 00 00 00 00 01 00  03 00 e7 3c ed 03 00 00  |...........<....|
000000f0  80 00 00 00 20 00 00 1a  00 00 00 00 00 00 00 00  |.... ...........|
00000100  00 00 00 00 00 00 01 00  07 00 14 00 ff 01 0f 00  |................|
00000110  80 00 00 00 20 00 00 1a  20 00 00 00 00 00 00 00  |.... ... .......|
00000120  0f 00 00 00 00 00 0f 00  00 00 00 00 00 00 00 00  |................|
00000130  80 00 00 00 20 00 00 1a  28 0e 04 00 00 00 00 00  |.... ...(.......|
00000140  15 00 00 00 00 00 16 00  00 00 00 00 00 00 00 00  |................|
00000150  80 00 00 00 20 00 00 1a  50 0e 04 00 00 00 00 00  |.... ...P.......|
00000160  14 00 00 00 00 00 15 00  00 00 00 00 00 00 00 00  |................|
00000170  80 00 00 00 20 00 00 1a  74 0e 04 00 00 00 00 00  |.... ...t.......|
00000180  13 00 00 00 00 00 14 00  00 00 00 00 00 00 00 00  |................|
00000190  80 00 00 00 20 00 00 1a  03 48 04 00 00 00 00 00  |.... ....H......|
000001a0  12 00 00 00 00 00 13 00  00 00 00 00 00 00 00 00  |................|
000001b0  80 00 00 00 20 00 00 1a  0c 48 04 00 00 00 00 00  |.... ....H......|
000001c0  11 00 00 00 00 00 12 00  00 00 00 00 00 00 00 00  |................|
000001d0  80 00 00 00 20 00 00 1a  22 48 04 00 00 00 00 00  |.... ..."H......|
000001e0  10 00 00 00 00 00 01 00  00 00 00 00 00 00 00 00  |................|
000001f0  b0 00 00 00 20 00 00 1a  00 00 00 00 00 00 e6 20  |.... .......... |
00000200
```

---

### Post by caljohnsmith on 2009-02-15
OK, I think I see at least part of the problem; your sda3 Ubuntu partition is listed as "LVM" in the partition table even though it is an ext2 partition. How about doing the following:
```
sudo sfdisk -c /dev/sda 3 83
```
Then try reinstalling Ubuntu again, and go ahead and use ext2 for the file system again; also make sure you check the "format partition" box for sda3 when you reinstall. Please let me know how that goes.

---

### Post by backfour94 on 2009-02-15
Now we're cooking.

Installed this time and I'm answering this from Firefox on a proper boot.

Thanks very very much.

Can I leave it as it is or should I change the ext2 partition?

---

### Post by caljohnsmith on 2009-02-15
That's great news, glad Ubuntu finally installed OK. I would recommend going ahead and upgrading to ext3, so how about doing:
```
sudo tune2fs -j /dev/sda3
gksudo gedit /etc/fstab
```
Find the line in your fstab that shows your sda3 partition (it will show a mount point of "/"), and change the file system from ext2 to ext3 on that line. Let me know how that goes or if you run into problems.

---

### Post by backfour94 on 2009-02-15
Ok I'll give it a go.  But I probably won't be able to get to it until tomorrow evening, UK time c19.00.

Thanks for all you help so far.

---

### Post by murthy on 2009-06-27
I am also having the same problem, kindly suggest a solution. Running 
sudo sfdisk -c /dev/sda 8 83 has not solved the problem.  the text of results.txt is
> ```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #8 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ee5e3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   164,103,974   164,103,912   7 HPFS/NTFS
/dev/sda2         164,103,975 2,930,272,064 2,766,168,090   f W95 Ext d (LBA)
/dev/sda5         164,104,038 2,271,928,364 2,107,824,327   7 HPFS/NTFS
/dev/sda6       2,271,928,428 2,878,928,324   606,999,897   7 HPFS/NTFS
/dev/sda7       2,878,928,388 2,887,137,539     8,209,152  82 Linux swap / Solaris
/dev/sda8       2,887,137,603 2,930,272,064    43,134,462  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="54D0CB1BD0CB01EA" TYPE="ntfs" 
/dev/sda5: UUID="F4981026980FE5C8" LABEL="New Volume" TYPE="ntfs" 
/dev/sda6: UUID="746DB7385E0A51EC" LABEL="newfolder" TYPE="ntfs" 
/dev/sda7: UUID="bde41ad7-3c01-4294-b719-2c60f1bd67d8" TYPE="swap" 
/dev/sda8: UUID="babc4495-3011-4f01-a4cc-288f4b62eab8" TYPE="ext2" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda8 on /target type ext2 (rw,relatime,errors=remount-ro)
/proc on /target/proc type none (rw,bind)
/dev on /target/dev type none (rw,bind)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=babc4495-3011-4f01-a4cc-288f4b62eab8 /               ext2    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=bde41ad7-3c01-4294-b719-2c60f1bd67d8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


1488.6GB: boot/grub/stage2
1488.7GB: boot/initrd.img-2.6.28-11-generic
1488.7GB: boot/vmlinuz-2.6.28-11-generic
1488.7GB: initrd.img
1488.7GB: vmlinuz
```

---

### Post by unutbu on 2009-06-27
It appears you are missing /boot/grub/menu.lst. 

What happens if you boot from the Jaunty LiveCD, open a terminal (Applications>Accessories>Terminal) and type

```
sudo mount /dev/sda8 /mnt  
cd /mnt
sudo mount --bind {/,}proc
sudo mount  --bind {/,}sys
sudo mount  --bind {/,}dev
sudo chroot /mnt
grep -v rootfs /proc/mounts> /etc/mtab
update-grub
```

This will regenerate /boot/grub/menu.lst.

After doing this, reboot and see if you can boot Ubuntu and Windows.
If it works, great. If not, please run boot_info_script again and post the new RESULTS.txt here.

---

### Post by murthy on 2009-06-28
I did as directed, but still no result.  "result.txt" contents are shown below  (now I installed jacky in sda7 and swap in sda8 )
> ```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ee5e3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   164,103,974   164,103,912   7 HPFS/NTFS
/dev/sda2         164,103,975 2,930,272,064 2,766,168,090   f W95 Ext d (LBA)
/dev/sda5         164,104,038 2,271,928,364 2,107,824,327   7 HPFS/NTFS
/dev/sda6       2,271,928,428 2,878,928,324   606,999,897   7 HPFS/NTFS
/dev/sda7       2,878,928,388 2,922,464,474    43,536,087  83 Linux
/dev/sda8       2,922,464,538 2,930,272,064     7,807,527  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="54D0CB1BD0CB01EA" TYPE="ntfs" 
/dev/sda5: UUID="F4981026980FE5C8" LABEL="New Volume" TYPE="ntfs" 
/dev/sda6: UUID="746DB7385E0A51EC" LABEL="newfolder" TYPE="ntfs" 
/dev/sda7: UUID="580539e9-698b-4499-85c2-b84fa5b62efa" TYPE="ext2" 
/dev/sda8: TYPE="swap" UUID="4f5985e6-153d-40a4-b9e8-597a5cbaccbc" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=580539e9-698b-4499-85c2-b84fa5b62efa ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=580539e9-698b-4499-85c2-b84fa5b62efa

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		580539e9-698b-4499-85c2-b84fa5b62efa
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=580539e9-698b-4499-85c2-b84fa5b62efa ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		580539e9-698b-4499-85c2-b84fa5b62efa
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=580539e9-698b-4499-85c2-b84fa5b62efa ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		580539e9-698b-4499-85c2-b84fa5b62efa
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=580539e9-698b-4499-85c2-b84fa5b62efa /               ext2    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=4f5985e6-153d-40a4-b9e8-597a5cbaccbc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


1490.4GB: boot/grub/menu.lst
1490.4GB: boot/grub/stage2
1490.5GB: boot/initrd.img-2.6.28-11-generic
1490.5GB: boot/vmlinuz-2.6.28-11-generic
1490.5GB: initrd.img
1490.5GB: vmlinuz
```

---

### Post by unutbu on 2009-06-28
The RESULTS.txt suggests you have reinstalled Jaunty (and in the process swapped sda7 and sda8). It also shows GRUB has been overwritten with the Windows bootloader on sda. 

Try this:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by murthy on 2009-07-04
All this failed with the same problem.  I have now installed debian5 which installed without any problem.  Anyway thanks!

---

### Post by murthy on 2009-07-10
Any help for future use?

---

### Post by murthy on 2009-09-04
Any help? please.

---

