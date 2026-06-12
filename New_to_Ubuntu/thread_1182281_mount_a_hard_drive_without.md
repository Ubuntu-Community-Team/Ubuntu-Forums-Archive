---
title: "mount a hard drive without"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by cmaranhao on 2009-06-08
[IMG]http://img195.imageshack.us/my.php?image=96509387.png[/IMG]

i want to mount that specific drive in my root but don't know how to do it.. maybe someone here can help me?

i formated my other drives and i already mounted all of them but i cannot do it to that specific drive (it has a lot of data and was not formatted!!!).

can someone help me?

when i input sudo fdisk-l it outputs the following:

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x73eee67d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        9728    62782020    f  W95 Ext'd (LBA)
/dev/sda5            1913        3824    15358108+  83  Linux
/dev/sda6            3825        9728    47423848+  83  Linux

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 17.3 GB, 17340000256 bytes
255 heads, 63 sectors/track, 2108 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde65de65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         243     1951866   82  Linux swap / Solaris
/dev/sdc2             244        2108    14980612+  83  Linux

notice that sdb (my 200GB hard drive) is stated as an invalid partition table. can i mount the drive and recover the data? how?

i am not experienced in linux

---

### Post by louieb on 2009-06-08
I would try a program called **testdisk**, its in the repositories. The newest version and how to use it can be found here.  [SystemRescueCd]("http://www.sysresccd.org/Main_Page")

What it does is check the drive and try to rebuild the partition table.

---

### Post by cmaranhao on 2009-06-08
> **louieb said:**
> I would try a program called **testdisk**, its in the repositories. The newest version and how to use it can be found here.  [SystemRescueCd]("http://www.sysresccd.org/Main_Page")

What it does is check the drive and try to rebuild the partition table.

all that it does is to check the drive? i have very important data in that drive and i cannot afford to lose it. read the description and it seems easy to use. too bad i don't have any cd's here to try this. is there any other way?

---

### Post by nandemonai on 2009-06-08
> **cmaranhao said:**
> all that it does is to check the drive? i have very important data in that drive and i cannot afford to lose it. read the description and it seems easy to use. too bad i don't have any cd's here to try this. is there any other way?

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

As stated before it attempts to rebuild partition tables not just checks the disk.

You can get it via apt, no need for a CD.

```
sudo apt-get install testdisk
```

Good luck with the recovery.

---

### Post by Hund on 2009-06-08
You could use Gparted to check and correct any errors.

---

### Post by Miljet on 2009-06-08
> (it has a lot of data and was not formatted!!!

I can assure you that if this disk contains data, it was formatted. You cannot store date on a disk that has not been formatted. The partition table appears to have been corrupted.

As others have already pointed out, there are numerous ways to attempt to repair a partition table. But there are no guarantees that any of them will work. That is why we always encourage everyone to make backups.

Good luck.

---

### Post by cmaranhao on 2009-06-09
i had all the data stored yesterday and formatted all my other drives because i wanted to upgrade to ubuntu 9.04.

although when formatting with my windows XP disc (i have dual boot now), i accidentally pressed D in that drive (it then asked me that if i wanted to erase the content i had to press L).. obviously i canceled!

then i installed windows in the wanted partition.

when installing ubuntu, i was able "to see" all my drives so i specified where i wanted the file system to be installed and the swap. the other partitions i made using the EXT3 mode. now i have them mounted using the method i used a few years ago.

that specific drive (my 200 gb backup drive) didn't had the same options as the other drives. it was greyed out and i didn't do anything to it once again!

i will need help here because i have lots of work in there from university, from my actual job and lots of personal content like photos of someone that unfortunately is not among us anymore. this is why i say i cannot afford to lose the data.

can someone please help me? i haven't touched the drive at all (although i came close when i pressed D in windows installer by mistake but cancelled right after).

---

### Post by LewRockwell on 2009-06-09
Hi,

Sorry to hear about your difficulties. Sometimes when we're doing the "clicky-clicky" we select something we do NOT want to do. Almost everyone who messes with computers has had this OMG moment. You're not the first and you definitely won't be the last.

It should also be noted that, for the sake of brevity in the forums, most of those offering you assistance and suggestions will ASSUME that you have done "due diligence" and that you have "off-machine" back-up/clones of ALL your important data. Please keep this in mind FOREVER, wherever your travels take you across the vast universe that is the world wide web.

I recommend that you use Testdisk.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

This will require some self-educating on your part as you learn how this software can rescue you and fix your difficulties. As you can see from the documentation, you will need to know what the file system(s) and partitions were BEFORE this particular situation presented itself.

As always, your mileage may vary depending on your driving habits.

Never give up, never surrender!

---

### Post by cmaranhao on 2009-06-09
can someone help me to install testdisk?

i don't know how to do it.

---

### Post by Hund on 2009-06-09
Open the "Terminal" under "Applications / Accesories" and type this:

> sudo aptitude install testdisk

Or use Synaptic under "System / Administration.

---

### Post by cmaranhao on 2009-06-09
> **Hund said:**
> Open the "Terminal" under "Applications / Accesories" and type this:



Or use Synaptic under "System / Administration.

thanks, i installed it but where did it go? i want to try and recover my data now.. it was EXT3.

---

### Post by cmaranhao on 2009-06-09
i don't know if it is a coincidence but just noticed that under places i have the 200GB hard drive and all my data is in there!!!

just went to gparted and it says that my drive is EXT3! so nice :)

i am SOOOOOOOO HAPPPPPYYYYYYY!!!!

just one final question. i want to mount this drive inside my home folder named multimedia. how do i do it?

i will do a backup right away. i just cannot afford to lose my content. too valuable, especially my photos.

---

### Post by Hund on 2009-06-09
List your disks and partitions:

> sudo fdisk -l

You will ge a output that looks someting like this:

> Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008aec4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

The partition for me is "sdb1", lets get the UUID from it:

> sudo vol_id -u /dev/sdb1

Open up your fstab file:

> gksudo gedit /etc/fstab

And add this line at the bottom:

>     UUID=7aa63d5b-aa1a-4f52-bd07-ab1d4ec15eff /home/hund/multimedia     ext3    defaults        0       2

Dont forget to change the UUID to the one your partition have and the correct username. But I would recomend mounting stuff under "/media", i.e: "/media/multimedia".

---

