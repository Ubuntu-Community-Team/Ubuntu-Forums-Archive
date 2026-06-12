---
title: "Can't find an existing ntfs RAID5 partion"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by jonrea on 2009-07-12
Hi,

I thought I'd try out ubuntu for a media server PC I've had running vista previously.  I have a RAID5 (4 x 1TB hard drives) array that was working in vista and a boot hard disk (IDE).  The RAID has a significant amount of data on it so I don't want to format.

I managed to install ubuntu x64 server onto the single hard disk without too many issues though I don't seem to be able to access the RAID - when I ls /dev/mapper/ it shows the following:

```
jon@store:~$ ls /dev/mapper/
control  nvidia_cgajbdcf  store-root  store-swap_1
```

Now as I understand it the "nvidia_cgajbdcf" entry is the whole RAID array, though there don't seem to be any partitions found - which is odd since it was working under vista.

Originally I was using 9.04 (Jaunty) but I've changed to 8.10 (Intrepid) after browsing the forums and seeing that some people were having trouble with the RAID5 support in 9.04.

Useful info (I believe):

```
jon@store:~$ sudo dmraid -ay
[sudo] password for jon:
RAID set "nvidia_cgajbdcf" already active

jon@store:~$ sudo dmraid -r
/dev/sdd: nvidia, "nvidia_cgajbdcf", raid5_ls, ok, 1953525166 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_cgajbdcf", raid5_ls, ok, 1953525166 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_cgajbdcf", raid5_ls, ok, 1953525166 sectors, data@ 0
/dev/sda: nvidia, "nvidia_cgajbdcf", raid5_ls, ok, 1953525166 sectors, data@ 0

jon@store:~$ cat /proc/partitions
major minor  #blocks  name

   8     0  976762584 sda
   8    16  976762584 sdb
   8    32  976762584 sdc
   8    48  976762584 sdd
   8    64  293057352 sde
   8    65  292808691 sde1
   8    66          1 sde2
   8    69     240943 sde5
 254     0  286736384 dm-0
 254     1    6070272 dm-1
 254     2 2930287680 dm-2
jon@store:~$ cat /proc/mounts
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw,mode=755 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
/dev/mapper/store-root / ext3 rw,relatime,errors=remount-ro,data=ordered 0 0
/dev/mapper/store-root /dev/.static/dev ext3 ro,errors=remount-ro,data=ordered 0
 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=755 0 0
varrun /var/run tmpfs rw,nosuid,mode=755 0 0
varlock /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,nosuid,noexec,gid=5,mode=620 0 0
/dev/sde5 /boot ext3 rw,relatime,errors=continue,data=ordered 0 0
securityfs /sys/kernel/security securityfs rw 0 0

jon@store:~$ sudo parted /dev/mapper/nvidia_cgajbdcf
GNU Parted 1.8.9
Using /dev/mapper/nvidia_cgajbdcf
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Model: Linux device-mapper (dm)
Disk /dev/mapper/nvidia_cgajbdcf: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags

 1      17.4kB  134MB   134MB                Microsoft reserved partition  msftr
es
 2      135MB   3001GB  3000GB  ntfs         Basic data partition


```

From what I've picked up I believe that the partition is there but it's not being picked up by ubuntu to give me a link to it that I can then mount.

Sorry if I've not been too clear (bit of a noob) but I'd appreciate any help or advice, since I've been messing around with this for the best part of the weekend.

Thanks for any help.

Jon

---

### Post by Delever on 2009-07-12
Did your Vista system required driver to set up RAID? If so, such driver is required for Linux too, but Linux might not have it. You need to search for similar successful setups on google.

What I know: RAID systems provided by motherboard manufacturers usually do all their work on CPU, most of it - on drivers. 
Software RAID is provided by linux kernel and does not need any additional drivers - only available disks. However, I think such RAID would not work on Windows.

To install Linux software RAID, use alternate Ubuntu CD. But since RAID setups do not easily mix together between different operating systems, you need to find solution that is either supported by both systems (I can't help much here), or to use single system.

---

### Post by jonrea on 2009-07-12
Thanks for your reply.

I thought it might be something like that.  I did need the nvidia raid drivers to install in vista but I hoped that dmraid might be able to read the data and do the job of the driver, it seem to have been used successfully by others.  

As far as I can tell dmraid recognises that there's a volume there and parted can recognise the partition but the link to the partition doesn't appear in the mapper directory.

---

### Post by jonrea on 2009-07-13
So it looks like my only option is to go back to Vista, either permently or at least to get the data - assuming I can find the space elsewhere to back it all up.

---

