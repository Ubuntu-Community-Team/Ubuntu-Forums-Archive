---
title: "Vista, Ubuntu, Secondary HD (USB), Pain.."
date: 2010-01-08
forum: New to Ubuntu
---

### Post by hungryOrb on 2010-01-08
Hi..

Installing Ubuntu 9.10 to the secondary stopped vista from loading in GRUB, and gets an error. Also doesn't load Ubuntu either.
Really would like to get GRUB to load both, and at the moment, the only hope is the LIVE CD. Alternatively, downloading the Vista recovering disk and running that through a USB stick (boot) would be ok. But then wouldn't have Ubu..! 

Please GRUB experts! Help!

---

### Post by presence1960 on 2010-01-08
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB with your external HDD plugged in.. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Schpwuette on 2010-01-08
Hi, patient here.

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=6fb71692-919d-4f8c-a922-aeb48ce248d9)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdd
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
129 heads, 4 sectors/track, 605778 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf98d6e74

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    14,338,047    14,336,000  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     14,338,048   312,578,047   298,240,000   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250057252864 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488393072 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000762d5

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,392,064   488,392,002   c W95 FAT32 (LBA)


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 262 MB, 262144000 bytes
9 heads, 56 sectors/track, 1015 cylinders, total 512000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

sda1: LABEL="RECOVERY" UUID="80E9-C15B" TYPE="vfat" 
sdb1: LABEL="" UUID="5E60-5322" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdd on /media/74F2-0E4F type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdd

00000000  eb 58 90 6d 6b 64 6f 73  66 73 00 00 02 01 20 00  |.X.mkdosfs.... .|
00000010  02 00 00 00 00 f8 00 00  38 00 09 00 00 00 00 00  |........8.......|
00000020  00 d0 07 00 63 0f 00 00  00 00 00 00 02 00 00 00  |....c...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 4f 0e f2 74 20  20 20 20 20 20 20 20 20  |..)O..t         |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda2

00000000  33 c0 8e d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |3.....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 07 8b  |...It.8,t.......|
00000040  f0 ac 3c 00 74 fc bb 07  00 b4 0e cd 10 eb f2 88  |..<.t...........|
00000050  4e 10 e8 46 00 73 2a fe  46 10 80 7e 04 0b 74 0b  |N..F.s*.F..~..t.|
00000060  80 7e 04 0c 74 05 a0 b6  07 75 d2 80 46 02 06 83  |.~..t....u..F...|
00000070  46 08 06 83 56 0a 00 e8  21 00 73 05 a0 b6 07 eb  |F...V...!.s.....|
00000080  bc 81 3e fe 7d 55 aa 74  0b 80 7e 10 00 74 c8 a0  |..>.}U.t..~..t..|
00000090  b7 07 eb a9 8b fc 1e 57  8b f5 cb bf 05 00 8a 56  |.......W.......V|
000000a0  00 b4 08 cd 13 72 23 8a  c1 24 3f 98 8a de 8a fc  |.....r#..$?.....|
000000b0  43 f7 e3 8b d1 86 d6 b1  06 d2 ee 42 f7 e2 39 56  |C..........B..9V|
000000c0  0a 77 23 72 05 39 46 08  73 1c b8 01 02 bb 00 7c  |.w#r.9F.s......||
000000d0  8b 4e 02 8b 56 00 cd 13  73 51 4f 74 4e 32 e4 8a  |.N..V...sQOtN2..|
000000e0  56 00 cd 13 eb e4 8a 56  00 60 bb aa 55 b4 41 cd  |V......V.`..U.A.|
000000f0  13 72 36 81 fb 55 aa 75  30 f6 c1 01 74 2b 61 60  |.r6..U.u0...t+a`|
00000100  6a 00 6a 00 ff 76 0a ff  76 08 6a 00 68 00 7c 6a  |j.j..v..v.j.h.|j|
00000110  01 6a 10 b4 42 8b f4 cd  13 61 61 73 0e 4f 74 0b  |.j..B....aas.Ot.|
00000120  32 e4 8a 56 00 cd 13 eb  d6 61 f9 c3 49 6e 76 61  |2..V.....a..Inva|
00000130  6c 69 64 20 70 61 72 74  69 74 69 6f 6e 20 74 61  |lid partition ta|
00000140  62 6c 65 00 45 72 72 6f  72 20 6c 6f 61 64 69 6e  |ble.Error loadin|
00000150  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
00000160  65 6d 00 4d 69 73 73 69  6e 67 20 6f 70 65 72 61  |em.Missing opera|
00000170  74 69 6e 67 20 73 79 73  74 65 6d 00 00 00 00 00  |ting system.....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 2c 44 63  4d 47 52 20 69 73 20 63  |.....,DcMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc
```The 'sdc' is the USB stick.

---

### Post by presence1960 on 2010-01-08
> **Schpwuette said:**
> Hi, patient here.

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=6fb71692-919d-4f8c-a922-aeb48ce248d9)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdd
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
129 heads, 4 sectors/track, 605778 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf98d6e74

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    14,338,047    14,336,000  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     14,338,048   312,578,047   298,240,000   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250057252864 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488393072 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000762d5

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,392,064   488,392,002   c W95 FAT32 (LBA)


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 262 MB, 262144000 bytes
9 heads, 56 sectors/track, 1015 cylinders, total 512000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

sda1: LABEL="RECOVERY" UUID="80E9-C15B" TYPE="vfat" 
sdb1: LABEL="" UUID="5E60-5322" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdd on /media/74F2-0E4F type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdd

00000000  eb 58 90 6d 6b 64 6f 73  66 73 00 00 02 01 20 00  |.X.mkdosfs.... .|
00000010  02 00 00 00 00 f8 00 00  38 00 09 00 00 00 00 00  |........8.......|
00000020  00 d0 07 00 63 0f 00 00  00 00 00 00 02 00 00 00  |....c...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 4f 0e f2 74 20  20 20 20 20 20 20 20 20  |..)O..t         |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda2

00000000  33 c0 8e d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |3.....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 07 8b  |...It.8,t.......|
00000040  f0 ac 3c 00 74 fc bb 07  00 b4 0e cd 10 eb f2 88  |..<.t...........|
00000050  4e 10 e8 46 00 73 2a fe  46 10 80 7e 04 0b 74 0b  |N..F.s*.F..~..t.|
00000060  80 7e 04 0c 74 05 a0 b6  07 75 d2 80 46 02 06 83  |.~..t....u..F...|
00000070  46 08 06 83 56 0a 00 e8  21 00 73 05 a0 b6 07 eb  |F...V...!.s.....|
00000080  bc 81 3e fe 7d 55 aa 74  0b 80 7e 10 00 74 c8 a0  |..>.}U.t..~..t..|
00000090  b7 07 eb a9 8b fc 1e 57  8b f5 cb bf 05 00 8a 56  |.......W.......V|
000000a0  00 b4 08 cd 13 72 23 8a  c1 24 3f 98 8a de 8a fc  |.....r#..$?.....|
000000b0  43 f7 e3 8b d1 86 d6 b1  06 d2 ee 42 f7 e2 39 56  |C..........B..9V|
000000c0  0a 77 23 72 05 39 46 08  73 1c b8 01 02 bb 00 7c  |.w#r.9F.s......||
000000d0  8b 4e 02 8b 56 00 cd 13  73 51 4f 74 4e 32 e4 8a  |.N..V...sQOtN2..|
000000e0  56 00 cd 13 eb e4 8a 56  00 60 bb aa 55 b4 41 cd  |V......V.`..U.A.|
000000f0  13 72 36 81 fb 55 aa 75  30 f6 c1 01 74 2b 61 60  |.r6..U.u0...t+a`|
00000100  6a 00 6a 00 ff 76 0a ff  76 08 6a 00 68 00 7c 6a  |j.j..v..v.j.h.|j|
00000110  01 6a 10 b4 42 8b f4 cd  13 61 61 73 0e 4f 74 0b  |.j..B....aas.Ot.|
00000120  32 e4 8a 56 00 cd 13 eb  d6 61 f9 c3 49 6e 76 61  |2..V.....a..Inva|
00000130  6c 69 64 20 70 61 72 74  69 74 69 6f 6e 20 74 61  |lid partition ta|
00000140  62 6c 65 00 45 72 72 6f  72 20 6c 6f 61 64 69 6e  |ble.Error loadin|
00000150  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
00000160  65 6d 00 4d 69 73 73 69  6e 67 20 6f 70 65 72 61  |em.Missing opera|
00000170  74 69 6e 67 20 73 79 73  74 65 6d 00 00 00 00 00  |ting system.....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 2c 44 63  4d 47 52 20 69 73 20 63  |.....,DcMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc
```The 'sdc' is the USB stick.

Your sda2 is windows and is unmountable. Where is sdc and what is supposed to be on that? It obviously was not plugged in when you ran the script.

How and where did you install Ubuntu? Did you install it via wubi or did you boot the Live CD and install it? Where did you install it to?

I need more info here.

---

### Post by Schpwuette on 2010-01-08
The 'sdc' was right at the bottom. I noted it in case you'd wonder. But after looking at the results again... I see 'sdd' is the USB stick. So I don't know what 'sdc' is. Nevermind.

I installed Ubuntu via the Live CD, onto a free space partition in the spare (USB) hard disk. That would be 'sdb'.
Somewhere along the line, 'sdb' got fused back into one partition. I'm not sure when or how.

When installing Ubuntu... I did it from the 'test without affecting your computer' desktop. Both hard disks were on at the time. As I said, I installed it onto the spare.
The installation completed successfully, and it asked me to reboot and eject the CD.
I did so, and made my computer boot from the spare. I got the message:
GRUB LOADING
error: disk doesn't exist (slight paraphrase there...)
grub rescue>
I switched off, disconnected the spare and tried to boot Vista, but got the same message.

Since then, the only thing I've been able to boot from is the Live CD.

I could probably tell you more, but I don't know what information is necessary...


immediate edit: Ah, you say the Vista partition is unmountable? Strange, because before the install it was mountable.

---

### Post by presence1960 on 2010-01-08
> **Schpwuette said:**
> The 'sdc' was right at the bottom. I noted it in case you'd wonder. But after looking at the results again... I see 'sdd' is the USB stick. So I don't know what 'sdc' is. Nevermind.

I installed Ubuntu via the Live CD, onto a free space partition in the spare (USB) hard disk. That would be 'sdb'.
Somewhere along the line, 'sdb' got fused back into one partition. I'm not sure when or how.

When installing Ubuntu... I did it from the 'test without affecting your computer' desktop. Both hard disks were on at the time. As I said, I installed it onto the spare.
The installation completed successfully, and it asked me to reboot and eject the CD.
I did so, and made my computer boot from the spare. I got the message:
GRUB LOADING
error: disk doesn't exist (slight paraphrase there...)
grub rescue>
I switched off, disconnected the spare and tried to boot Vista, but got the same message.

Since then, the only thing I've been able to boot from is the Live CD.

I could probably tell you more, but I don't know what information is necessary...


immediate edit: Ah, you say the Vista partition is unmountable? Strange, because before the install it was mountable.

If you installed to sdb it is gone now because the whole disk is a FAT partition, Ubuntu uses ext3 or ext4 usually and a few other filesystems but definitely not a windows filesystem.

At this point since you tried to install to an external hard disk I would try to repair Vista by downloading an iso from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and burning it as an image to CD. Boot from that CD and follow the instructions here for Vista. Hopefully that will restore Vista to MBR and you will be able to boot into Vista.

If that works then try installing Ubuntu to the external disk again. This time use correct filesystem and when you reach the Ready to install window pictured below click the advanced button and choose to put GRUB on MBR of the external disk. (should be /dev/sdb- but make sure!)

Then when it is installed and you reboot go into BIOS and set USB/Removable to boot before hard disk in the device boot order. Save changes to CMOS and continue booting.

Now when you start your machine without the external plugged in windows will boot because it is on MBR of internal disk (sda) and when you boot with the external plugged in GRUB will take over because it is on MBR of the external and you can boot into Ubuntu.

---

### Post by Schpwuette on 2010-01-09
I see... Thanks. I see where I went wrong now.
There is but one problem. I only have one disk drive, and I assume I need the Live CD in it to be able to do anything. So I can't burn the recovery disk. Do you know a way to make a USB stick bootable with the recovery disk? The only program I could find (that works in Ubuntu) was one that could only do it for the Live CD iso. And my USB stick isn't big enough for that.

However... I could use the spare. But I'm hesitant to mess with it at the moment because I don't know where the data that was on it has gone. It should have Ubuntu + ~150gb of miscellaneous stuff on it. Is that gone for good? Or is it recoverable? What happened to it?
Am I asking too much of you?

---

