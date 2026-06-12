---
title: "Connecting to NAS through wireless router"
date: 2014-10-17
forum: Networking &amp; Wireless
---

### Post by erikstrawn on 2014-10-17
I got my brand new router and 4TB drive, and now I'm trying to connect to the drive with my Ubuntu 12.04 computers. I connect to the router just fine and I can surf here and tweak the router settings with my browser like normal. My daughter's Win7 netbook connects fine and shows the drive as \\192.168.xxx.xxx\Seagate Expansi, but I've tried following instructions elsewhere on the forum and haven't made any progess. I installed cifs, tried changing settings in fstab, and tried a dozen different variants of the mount command and still didn't get anywhere.

sudo fdisk -l
...gives the following...

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008f5b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   969211903   484604928   83  Linux
/dev/sda2       969213950   976771071     3778561    5  Extended
/dev/sda5       969213952   976771071     3778560   82  Linux swap / Solaris


sudo smbclient -L 192.168.xxx.xxx
...gives the following...

Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.28a]
Server requested LANMAN password (share-level security) but 'client lanman auth = no' or 'client ntlmv2 auth = yes'
tree connect failed: NT_STATUS_ACCESS_DENIED

Ideas?

---

### Post by erikstrawn on 2014-10-18
I'd rebooted twice yesterday and when I clicked on "Browse Network" it always showed "Windows Network" and I couldn't go any farther. I turned on my laptop and it showed all the devices on the network and went into the network drive just fine. This morning this computer started seeing it. Not sure why it took 8 hours, but it's all up and running.

---

