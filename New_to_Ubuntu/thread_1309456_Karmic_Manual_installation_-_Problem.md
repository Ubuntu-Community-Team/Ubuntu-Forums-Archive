---
title: "Karmic Manual installation - Problem"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by keech on 2009-11-01
Hi, 

I manually upgraded from 9.04 to 9.10 by following the steps in my previous thread.

[http://ubuntuforums.org/showthread.php?t=976405]("http://ubuntuforums.org/showthread.php?t=976405") 

It worked perfectly for the previous installation from 8.10 to 9.04. But the present installation does not give me the same result. The partition utility ( I think it is the same GParted) does not recognise the 'sda' partition or it is throwing an error. Instead, there is some new disk partition names. Once, I install on this partition and restart the machine. There is a blank screen after the splash screen. I am attaching the screenshot below. Please help.

---

### Post by kansasnoob on 2009-11-01
Please follow the steps in this link and post the results of the Boot Info Script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by keech on 2009-11-01
Hi,

Thanks for the effort.

Please find the Results.txt output

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000a8f9

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *    147,701,610   222,082,559    74,380,950   5 Extended
/dev/sda5         147,701,673   218,933,819    71,232,147  83 Linux
/dev/sda6         218,933,883   222,082,559     3,148,677  82 Linux swap / Solaris
/dev/sda2          73,850,805   147,701,609    73,850,805   7 HPFS/NTFS
/dev/sda3                  63    73,850,804    73,850,742   7 HPFS/NTFS
/dev/sda4         222,082,560   312,576,704    90,494,145   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda: TYPE="nvidia_raid_member" 
/dev/mapper/nvidia_cfbjfjja2: UUID="6198871406D09638" LABEL="Disk2" TYPE="ntfs" 
/dev/mapper/nvidia_cfbjfjja3: UUID="1F24E1EE21DF348E" LABEL="Disk3" TYPE="ntfs" 
/dev/mapper/nvidia_cfbjfjja4: UUID="1254B0FE54B0E61F" LABEL="Disk4" TYPE="ntfs" 
/dev/mapper/nvidia_cfbjfjja5: UUID="7868eeb9-7ef7-4ae6-bca7-e016ec02ce01" TYPE="ext4" 
/dev/mapper/nvidia_cfbjfjja6: UUID="0dc71668-5c5f-4d87-97dc-47e5e6276f19" TYPE="swap" 

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

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda5


Unknown BootLoader  on sda6


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory

---

### Post by keech on 2009-11-01
Bump..Is there no one who is aware of the solution????????

---

### Post by ranch hand on 2009-11-01
I think a start to a solution would be to check all of your partitions with a LiveCD and see if they really are populated.  Just look at them with the menu.  Do they look normal?

Can you boot to this at all?  In recovery?  See a menu?

---

### Post by kansasnoob on 2009-11-02
> **keech said:**
> Bump..Is there no one who is aware of the solution????????

Sorry this slipped by me when I checked my posts this AM. Give me a little bit to parse all the info.

Expect more questions.

---

### Post by kansasnoob on 2009-11-02
Are you currently running the Live CD?

If so post a new screenshot of Gparted.

---

### Post by keech on 2009-11-02
hi kansasnoob,

Please see my first post for the screenshot. I had already uploaded it for reference.

---

### Post by keech on 2009-11-07
Bump... no one to help

---

### Post by quinnten83 on 2009-11-07
i thinkno one knows the answer really.
i can only see that none of the partition types are recognized.
Have you filed a  bug yet? maybe one of the developers know.
and does it work from live cd?
remember we help each other out, but we are not all guru's.

---

