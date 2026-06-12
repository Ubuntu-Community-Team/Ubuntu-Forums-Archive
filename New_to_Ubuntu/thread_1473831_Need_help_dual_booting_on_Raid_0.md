---
title: "Need help dual booting on Raid 0"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by MasterShihoChief on 2010-05-05
Ok so before this I was using Ubuntu 9.10 and dual booting with windows xp x64. I then went out and upgraded to 2 hdds and put them in a raid 0 array. I was able to install Windows 7 x64 ok and have been using it for months. 

Today I decided i wanted to dual boot once more with ubuntu x64 10.04. So i decrypted the drive(I was using truecrypt) and booted from the livecd and chose to install yet it wouldnt allow me to resize. It wanted to just wipe the whole drive and put ubuntu on it.

I booted from a gparted disc to try that and the partitoner wont allow me to resize the partiton. Has an exclamtion mark next to the main partiton on the array, and on the 300mb partition after it. I also get this error that is kinda long. Says it cant mount it or something. The windows partitioner wont resize more then a few gigs out of 400gb free, so ya im at a loss and hope u guys can help me get linux set up once again. Cheers

EDIT: I tried using gparted from within ubuntu livecd and it shows 2hdd and no raid >_<
and here is an fdisk -l (please note sdc1 is an external 2tb drive)

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb2d3fc8d

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x97f997f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121562   976444768+   7  HPFS/NTFS
/dev/sda2   *      121562      121601      307200    7  HPFS/NTFS

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0016dd90

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243202  1953513560    7  HPFS/NTFS
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 

```

also i am able to access the raid 0 from the live cd and run files from the raid no problem

EDIT 2: heres a screen shot of install
[IMG]http://i149.photobucket.com/albums/s65/MasterShihoChief/Screenshot.png[/IMG]

---

### Post by MasterShihoChief on 2010-05-06
I was able to defrag the windows partition and now windows partitoner allowed me to resize the raid volume and i now have 365gb unallocated space for ubuntu. I went to install. I set up ext4 volume 357gb with 8gb swap (2x my ram) but when it went to format the raid it immediately fails at ext4. The partition table is rewritten and shows everything is ok but ubuntu still refuses to install. I tried using ext3 instead of ext4 and still no luck. Im out of ideas now. Please help.

---

### Post by jbrown96 on 2010-05-06
How are you doing raid in Windows? Is it via a hardware card or your BIOS? If so, then it may work in Ubuntu, but many RAID cards won't work. 
If it is hardware RAID, then don't setup RAID in Ubuntu; your motherboard is automatically taking care of it. Just create the ext4 layout that you want.

---

### Post by MasterShihoChief on 2010-05-06
I assume it is a BIOS raid. I have to set to raid in bios and then set up the raid via the raid utility before boot. it says its a jmicron jmb36x raid controller but i doubt its a hardware raid.

---

### Post by jbrown96 on 2010-05-06
> **MasterShihoChief said:**
> I assume it is a BIOS raid. I have to set to raid in bios and then set up the raid via the raid utility before boot. it says its a jmicron jmb36x raid controller but i doubt its a hardware raid.

It's on the motherboard and is considered hardware raid. Try installing Ubuntu again, without doing raid in the installation. I would backup my data if I were; if those disks (/dev/sda and /dev/sdb) are showing up separately, then chances are that Ubuntu won't play nice with your raid setup.

---

### Post by MasterShihoChief on 2010-05-06
thats what i did. I put the regular live cd in and at the disk partitioning spot it shows Serial ATA 1.0TB Yggdrassil (Striped). I go manual partition and choose primary / ext4 partition and use 357GB and the remaining 8gb space for primary swap. It continues and i say install. It goes to 15% to set up the partitions and it says error unable to set up Yggdrassil/ARRAY5 ext4 format. If i click back the partiton table is absolutly fine and it shows a primary ext4 root partiton and the swap partition even though it said it failed. I cant install to it regardless and the windows partition manager sees the partitions as well. I have tried deleting the partitions and making it just unformated space on the drive to start over but it wont work. I guess maybe ubuntu just wont work nice with my raid then :(

---

