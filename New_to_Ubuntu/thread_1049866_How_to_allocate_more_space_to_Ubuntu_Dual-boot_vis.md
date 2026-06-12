---
title: "How to allocate more space to Ubuntu? Dual-boot vista and ubuntu"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by ronaldrand on 2009-01-25
Hello,

Today I installed dual-boot ubuntu on my Vista machine. I didn't really know if I would like Ubuntu so I only gave it 8 gigs of space. But now I'm starting to really like it and would like to allocate more.

I went into gparted expecting to see some ext3 or linux partitions, and all I see is NTFS parts. I went into Windows expecting to see something like that too, linux or unallocated, and all I have are NTFS partitions.

Am I confused? Doesn't Ubuntu create some linux partition when you install it? Here is the result of some common commands:

 sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd23d125d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17930   144022693+   7  HPFS/NTFS
/dev/sda2           17931       19457    12265627+   7  HPFS/NTFS


 sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      5.1G  3.3G  1.6G  68% /
tmpfs                 981M     0  981M   0% /lib/init/rw
varrun                981M  216K  980M   1% /var/run
varlock               981M     0  981M   0% /var/lock
udev                  981M  2.7M  978M   1% /dev
tmpfs                 981M  252K  980M   1% /dev/shm
/dev/sda1             138G  130G  8.1G  95% /host
lrm                   981M  2.0M  979M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/scd0              96M   96M     0 100% /media/GParted-live


How do I give Ubuntu more space to work with? Can anyone explain to me what I'm seeing? Thanks in advance.

---

### Post by Paqman on 2009-01-25
You installed Ubuntu using the [Wubi]("http://wubi-installer.org/") installer right? Wubi doesn't create any actual ext3 partitions, it creates a virtual hard drive that's really just a file on your NTFS partition.

Fear not though, the package [LVPM]("http://lubi.sourceforge.net/lvpm.html") can resize your virtual partition (scroll down to "Resizing virtual disks using LVPM")

---

### Post by ronaldrand on 2009-01-25
Thanks, that must be what I did. However, the LVPM does not give the option like in the instructions you provided. There is no resizeroot and resizehome. There is only resize. When I click on that, it begins resizing root. How can I resize home?

Edit: I might be jumping the gun and not giving it enough time, but it seems to be locking up sporadically. The first time I waited a few minutes as it seemed to do nothing, then the second time through it created the new image in no time and then began formatting it. But now it appears the formatting has locked up. Any idea about this?

---

