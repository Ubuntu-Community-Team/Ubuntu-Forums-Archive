---
title: "Need help reformating second HDD"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by Alexander86 on 2010-09-14
I have two hard drives in my computer. First I installed Windows XP, then I installed Ubuntu - Linux 10.04 LTS - the Lucid Lynx. 

Now I want to remove my second hard drive, but when I do that and start Linux it tells me that 6632872b-de81-4cc7-b900-c921b60fa04f is missing. I think that's the UUID of the second hard drive or a partition on that specific hard drive.

When I return everything to normal, and Linux starts up, the Disk Utility show me that there were two partitions on the second HDD. It's a 40G Drive, half of it I believe was a windows partition which easily came out, the second on is called 'Extended.'

Inside of 'Extended' is 'ext14' and 881M Free space. I installed GParted and it tells me that the 'Extended' File System is a part of /dev/sdb2 Partition and 'ext4' is /dev/sdb5 Partition. .../sdb5 is showing 10.89GiB used out of 17.82GiB Total.

When I try to unmount .../sdb5 it says
[INDENT]"[B]Could not unmount /dev/sdb5

[/B]The partition could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually."

[/INDENT]What can I do to get Linux to run with out this extra drive?

The reason I want to remove the drive is to put it into another computer.

Thank you.

---

### Post by amjjawad on 2010-09-14
> **Alexander86 said:**
> I have two hard drives in my computer. First I installed Windows XP, then I installed Ubuntu - Linux 10.04 LTS - the Lucid Lynx. 

Now I want to remove my second hard drive, but when I do that and start Linux it tells me that 6632872b-de81-4cc7-b900-c921b60fa04f is missing. I think that's the UUID of the second hard drive or a partition on that specific hard drive.

When I return everything to normal, and Linux starts up, the Disk Utility show me that there were two partitions on the second HDD. It's a 40G Drive, half of it I believe was a windows partition which easily came out, the second on is called 'Extended.'

Inside of 'Extended' is 'ext14' and 881M Free space. I installed GParted and it tells me that the 'Extended' File System is a part of /dev/sdb2 Partition and 'ext4' is /dev/sdb5 Partition. .../sdb5 is showing 10.89GiB used out of 17.82GiB Total.

When I try to unmount .../sdb5 it says[INDENT]"[B]Could not unmount /dev/sdb5

[/B]The partition could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually."

[/INDENT]What can I do to get Linux to run with out this extra drive?

The reason I want to remove the drive is to put it into another computer.

Thank you.

Ext4 is a Linux/Ubuntu file system. Where exactly you have installed Ubuntu? on which HDD? or in another word, what option you chose when you installed Ubuntu? Side by side? Erase and use the entire disk or advanced?

---

### Post by Alexander86 on 2010-09-14
Side by Side. I don't remember being given the option to choose which HDD to install to.

---

### Post by oldfred on 2010-09-14
Post this:
```

sudo fdisk -lu
```

---

### Post by Alexander86 on 2010-09-14
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xab48ab48

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488375999   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00045927

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2        39071742    78163967    19546113    5  Extended
/dev/sdb5        39071744    76443647    18685952   83  Linux

---

### Post by oldfred on 2010-09-14
It is not showing any sdb1 nor any swap. Just the extended with Linux installed in sdb. It looks like free space at the beginning of the drive. Did you have data there? If so, you may need to run testdisk to find missing partitions.

You only have one NTFS partition sda1 on sda, the 250GB drive. If XP you should be able to use gparted to shrink the partition and install Ubuntu into the free space. Be sure to leave windows with 20-30% free space or it will slow down or stop working as it needs room to work. 

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
Full Disk install Lucid Graphical
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Dual Boot Win7 & Ubuntu
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Older but similar:
Dual Boot win/Ubuntu
[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

---

### Post by Alexander86 on 2010-09-15
Great. Thank you. ^_^

---

