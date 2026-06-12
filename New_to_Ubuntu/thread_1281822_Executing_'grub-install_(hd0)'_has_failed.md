---
title: "Executing 'grub-install (hd0)' has failed"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by Marfish on 2009-10-03
Hello, I'm having some trouble with installing ubuntu on my Acer netbook. When I try to install it, it gets up to the point where it's installing the grub and then gives me the error message "Executing 'grub-install (hd0)' has failed. This is a faital error." I've tried using the tools to fix my mbr, because I thought that was the problem, with a windows recovery program that gives you lots of open source tools to fix windows. So far I am still getting the same error. Help would be very much appreciated.

---

### Post by arrange on 2009-10-03
We need more info on the error, but first - could you boot into a Ubuntu LiveCD, run the [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/") and post the results here?

Also - what version of Ubuntu are you trying to install?

---

### Post by Marfish on 2009-10-03
K, so I did the boot script. I'm trying to install desktop ubuntu 9.04 since the netbook remix img isn't even being recognized at bootup. I'm not trying to use the 250gb hard drive since it's an external.

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 8069 MB, 8069677056 bytes
217 heads, 4 sectors/track, 18157 cylinders, total 15761088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaead4529

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    15,757,311    15,755,264   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
1 heads, 63 sectors/track, 7752336 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01b38866

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,392,127   488,392,065   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="ACER" UUID="26EA-0E34" TYPE="vfat" 
/dev/mmcblk0p1: UUID="d73e9156-8fec-40e3-90f0-81ab2f80ec11" TYPE="ext3" 
/dev/mmcblk0p5: UUID="3023ee7f-ca72-4411-9cbd-66405e2c4e08" TYPE="swap" 
/dev/sdb1: UUID="3054B00B54AFD1C0" LABEL="Expansion Drive" TYPE="ntfs" 

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
/dev/mmcblk0p1 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/Expansion Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

[spybotsd]
timeout.old=30


================================ sda1/BOOT.INI: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

[spybotsd]
timeout.old=30

---

### Post by Marfish on 2009-10-03
*bump*

---

### Post by Marfish on 2009-10-04
*bump* help please. Anyone?

---

### Post by LewRockwell on 2009-10-04
> **Marfish said:**
> ```
K, so I did the boot script. I'm trying to install desktop ubuntu 9.04 since the netbook remix img isn't even being recognized at bootup. I'm not trying to use the 250gb hard drive since it's an external.

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 8069 MB, 8069677056 bytes
217 heads, 4 sectors/track, 18157 cylinders, total 15761088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaead4529

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    15,757,311    15,755,264   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
1 heads, 63 sectors/track, 7752336 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01b38866

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,392,127   488,392,065   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="ACER" UUID="26EA-0E34" TYPE="vfat" 
/dev/mmcblk0p1: UUID="d73e9156-8fec-40e3-90f0-81ab2f80ec11" TYPE="ext3" 
/dev/mmcblk0p5: UUID="3023ee7f-ca72-4411-9cbd-66405e2c4e08" TYPE="swap" 
/dev/sdb1: UUID="3054B00B54AFD1C0" LABEL="Expansion Drive" TYPE="ntfs" 

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
/dev/mmcblk0p1 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/Expansion Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

[spybotsd]
timeout.old=30


================================ sda1/BOOT.INI: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

[spybotsd]
timeout.old=30
```

looks like you are attempting to install Ubuntu on a flash card```
/dev/mmcblk0p1: UUID="d73e9156-8fec-40e3-90f0-81ab2f80ec11" TYPE="ext3"
```

our guess is that your particular Acer does not initiate the flash card drives as bootable devices

this causes the grub installation to fail because your /boot/grub/menu.lst file is on the flash card which is not available at boot time

here, you can see what we did with an Acer machine:

[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)


and here is a reference thread:

[http://ubuntuforums.org/showthread.php?t=981951](http://ubuntuforums.org/showthread.php?t=981951)


and here is another experience:

[http://www.osnews.com/story/20743/Eeebuntu_2_0_SD_Card_Installation_on_the_Aspire_One](http://www.osnews.com/story/20743/Eeebuntu_2_0_SD_Card_Installation_on_the_Aspire_One)

.

---

### Post by arrange on 2009-10-04
I don't understand a few things, maybe YOU can help me with those :)

1 in your profile - Gutsy Gibon?
2 IMO (and you're suggesting that too) Grub is installed last. The drive should have been repartitioned and files copied, but I don't see any Ubuntu partitions/files on either *sda* nor *sdb*?! 
3 How did you run the boot_info_script (from LiveCD)?

As a last resort, you can install Ubuntu **without** installing Grub, see if it goes through, and then install Grub separately.

---

### Post by LewRockwell on 2009-10-04
> **arrange said:**
> I don't understand a few things, maybe YOU can help me with those :)

1 in your profile - Gutsy Gibon?
2 IMO (and you're suggesting that too) Grub is installed last. The drive should have been repartitioned and files copied, but I don't see any Ubuntu partitions/files on either *sda* nor *sdb*?! 
3 How did you run the boot_info_script (from LiveCD)?

As a last resort, you can install Ubuntu **without** installing Grub, see if it goes through, and then install Grub separately.

looks like OP was attempting a flash card installation as per my post and links above

.

---

### Post by arrange on 2009-10-04
LR: Thanks, I accidently missed your post...

---

### Post by LewRockwell on 2009-10-04
> **arrange said:**
> LR: Thanks, I accidently missed your post...

it's all good

.

---

### Post by Marfish on 2009-10-08
Thanks a lot for all the help, I've now got ubuntu up and running. It seems you were right about my trying to install it on the other drive. I find it strange though, because both drives happen to be SD cards, just one happen to be the main harddrive. Anyways, runs way faster than it did on windows. Thanks again.

---

