---
title: "Multiple Hard Drives"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by simeoncastle on 2008-12-10
3-day-old Linux baby here.
Basically, when I finally worked out that it didnt like 6Gb of RAM it installed (4th time lucky...) I now find that it reads my first and second drives which are relatively low capacity, high r/w time drives but not my other two.
Interestingly, my Ubuntu is installed on my 3rd drive.
Anyway, I'm trying to get a huge download of something onto my big storage drive and it can't find it.
Does Linux have a cap on hard drives as it does Ram?
Any help massively appreciated!
Thanks

---

### Post by Rocket2DMn on 2008-12-10
The chances are the drive isn't mounted.  Can you please post the output from terminal of
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```
What size is the hard drive you are trying to get to?

---

### Post by 73ckn797 on 2008-12-10
4 hard drives with Intrepid is no problem here. one WinXP, one Intrepid 8.10, 2 general data/backup drives.

---

### Post by markbuntu on 2008-12-10
Are these drives all SATA drives or are some PATA or Raid?
I have 4 hard drives all SATA, 2 320GB, 1 160GB, 1 250GB with hardy i386, hardy amd64, intrepid amd64 and MAndriva 2009 on them with a bunch of partitions and unpartitioned free space. All the distros can see all the other drives and partitions.

---

### Post by modmadmike on 2008-12-10
"64-bit Linux allows up to 128 TB of address space for individual processes, and can address approximately 2[sup]46[/sup] (64 TB) of physical memory, subject to processor and system limitations." -Wikipedia

So if you Have x86_64 then 6gb should be no prob.

---

### Post by simeoncastle on 2008-12-11
Thanks to madmike for the 64bit comment, I'll get onto RAM once I've sorted the hard drives.

Hard drives, 320Gb and 1.5Tb respectively. All SATA, no RAID array althought may consider it in future... Maybe.
I'll just reboot & check Rockets command, hang about.
Ta :)

---

### Post by simeoncastle on 2008-12-11
Ookay, I won't ask for a translation, I'll get there when I'm good and ready, heh, but any layman's interpretation would be good - particularly bad headache right now so can't be sat too long staring at a screen.

simeon@simeon-desktop:~$ sudo fdisk -l
sudo: unable to resolve host simeon-desktop

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x64f930e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9040    72610816    7  HPFS/NTFS

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82d4fbe5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9040    72610816    7  HPFS/NTFS

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37cec0fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2   *           2      182401  1465128000    5  Extended
/dev/sdc5               2      182401  1465127968+   7  HPFS/NTFS

Disk /dev/sdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48bf55d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       48642   390709248    7  HPFS/NTFS
simeon@simeon-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
simeon@simeon-desktop:~$ sudo blkid
sudo: unable to resolve host simeon-desktop
/dev/sda1: UUID="9C76914076911C58" LABEL="Primary" TYPE="ntfs" 
/dev/sdb1: UUID="44667CD2667CC5E8" LABEL="Virtual Memory" TYPE="ntfs" 
/dev/sdc5: UUID="F7083C722CA633C5" LABEL="Slave Disk 2" TYPE="ntfs" 
/dev/sdd1: UUID="C4E8D4CFE8D4C13A" LABEL="Slave Disk 1" TYPE="ntfs" 
/dev/loop0: UUID="c5792e9a-6e08-4f1b-819a-ec47ebe887e1" TYPE="ext3" 
simeon@simeon-desktop:~$ mount
/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/simeon/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=simeon)

---

### Post by hyper_ch on 2008-12-11
(1) it's advised to use [noparse]```

```[/noparse] brackets around each output from a command or file content. That makes it easier to read.

(2) in addition also post the output of:
```

df -h

```

---

### Post by simeoncastle on 2008-12-11
Learning fast... *winces* Sorry, I'll take it onboard and improve.

---

### Post by Rocket2DMn on 2008-12-11
OK there is a lot of information there.  The mount command shows your root filesystem device as /host/ubuntu/disks/root.disk 
I assume this means you installed with Wubi?  I haven't it look quite like this before.

I see four other partitions of significance listed
```
/dev/sda1: UUID="9C76914076911C58" LABEL="Primary" TYPE="ntfs"
/dev/sdb1: UUID="44667CD2667CC5E8" LABEL="Virtual Memory" TYPE="ntfs"
/dev/sdc5: UUID="F7083C722CA633C5" LABEL="Slave Disk 2" TYPE="ntfs"
/dev/sdd1: UUID="C4E8D4CFE8D4C13A" LABEL="Slave Disk 1" TYPE="ntfs" 
```

Look at the label - do you recognize these names?  It looks like labels that you named yourself.
The sdc5 device and sdd1 device at 1.5TB and 400GB respectively.  The other 2 are 74GB each.  So let's say you are trying to get the 1.5TB drive to mount:

First create the mount point (this needs to be done only once).  We'll call the mountpoint "drive3", but you can call it whatever you want (no spaces or special characters):
```
sudo mkdir /media/drive3
```
Now try to mount manually:
```
sudo mount -t ntfs-3g /dev/sdc5 /media/drive3
```
Does it mount?  If it doesn't spit anything back out, then it should have mounted.  Let me know how this goes, and we'll proceed from there.

---

### Post by simeoncastle on 2008-12-15
Okay, I got through to it and mounted all 4 drives in similar technique, having followed the instruction to the letter and changing for each drive appropriately.
So now I have 4 drives, 2 called what they are usually called in Windows (the 2 74Gb drives) one called drive3 and the other is yet to appear.
But, it's progress :)

Yes, I installed with Wubi for reasons that escape me, I think it was because it was the easiest thing to do on a list of rather difficult and time-consuming things.
And yes, the labels are their respective handles in Windows.


```
simeon@simeon-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       27G  2.2G   24G   9% /
varrun               1014M  100K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M  100K 1014M   1% /dev
devshm               1014M   12K 1014M   1% /dev/shm
lrm                  1014M   38M  976M   4% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       27G  2.2G   24G   9% /home/simeon/.gvfs
/dev/sdc5             1.4T  232G  1.2T  17% /media/drive3
/dev/sda1              70G   52G   18G  75% /media/drive1
/dev/sdb1              70G   17G   53G  25% /media/drive2
/dev/sdd1             373G   29G  344G   8% /media/drive4

```

---

### Post by Rocket2DMn on 2008-12-15
It looks to me like all 4 drives are mounted to me.
/media/drive3
/media/drive1
/media/drive2
/media/drive4

---

### Post by Rocket2DMn on 2008-12-15
It looks to me like all 4 drives are mounted to me.
/media/drive3
/media/drive1
/media/drive2
/media/drive4

---

