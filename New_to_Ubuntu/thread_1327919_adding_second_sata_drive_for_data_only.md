---
title: "adding second sata drive for data only"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by northwestuntu on 2009-11-15
what would be the best way to format this drive?  this drive will only have data files.  

anyone know the best options for this?

thanks

---

### Post by dependancyhell on 2009-11-15
> **northwestuntu said:**
> what would be the best way to format this drive?  this drive will only have data files.  

anyone know the best options for this?

thanks

What do you want to access it with?

If you only need to access it with Linux, use EXT3.

If you need to use it with Windows, use NTFS.  Linux can read Windows drives, Windows can't (easily) read Linux drives.

---

### Post by Meskarune on 2009-11-15
which operating systems do you run? Do you want networked computers to access the data? What sort of backup system if any do you want to impliment?

FAT32 is the best option if you want to share data between different operating systems. you can even save firefox settings to the drive and use them in windows and linux.

---

### Post by northwestuntu on 2009-11-15
i will only be accessing it with linux.  no backup system. i back everything up on dvds that i really want.  i was gonna use gnome partition manager, but there are lots of options on it.

---

### Post by dependancyhell on 2009-11-15
> **northwestuntu said:**
> i will only be accessing it with linux.  no backup system. i back everything up on dvds that i really want.  i was gonna use gnome partition manager, but there are lots of options on it.


it doesn't matter what program you use to format with, it's just personal taste.

Gparted is nice and easy, there's no reason to change if that's what you were going to go with anyway.

Just right click on your new drive, Format As > Filesystem you want.

The EXTx are Linux filesystems (I'd go with EXT3 rather than 2 or 4, personally), Fat is Windows (and devices like MP3 players), and NTFS is Windows 2000 and above.

---

### Post by falconindy on 2009-11-15
XFS is a good choice for a larger file system that's only going to be storing data.

---

### Post by northwestuntu on 2009-11-16
create as primary or extended?

how do you mean for larger file system with Xfs?

---

### Post by northwestuntu on 2009-11-16
i should ask what the difference is between primary and extended?

---

### Post by lovinglinux on 2009-11-16
> **Meskarune said:**
> you can even save firefox settings to the drive and use them in windows and linux.

Not a good idea. There are several Firefox extensions that are OS dependent. The Mozilla Add-ons site offers the correct version according to your system. So sharing a profile between Windows and Linux could result in malfunctioning extensions or even profile corruption. If you want to share profiles between machines, use [Mozilla Labs - Weave Sync](https://addons.mozilla.org/en-US/firefox/addon/10868).

---

### Post by Paqman on 2009-11-16
> **northwestuntu said:**
> i should ask what the difference is between primary and extended?

Extended is like a container that you can create further partitions inside. This is used to get around the restriction of only having four partitions per disk.

---

### Post by mikechant on 2009-11-16
> i should ask what the difference is between primary and extended?

As you're using the whole disc for data, you just want one big primary partition. As per paqman's post above, you only need to use extended partitions when you need more than four partitions - for example, my Dell came with three partitions already (Windows boot, Windows Recovery, and Windows OS) so I shrank the Windows OS partition and used the space to create an extended partition. Inside the the extended partition I have various logical partitions for root, swap and /home for various Ubuntu releases etc. If you are interested wikipedia explains it further:
[http://en.wikipedia.org/wiki/Partition_table](http://en.wikipedia.org/wiki/Partition_table)

---

### Post by Funkey Monkey on 2009-11-16
> **mikechant said:**
> As you're using the whole disc for data, you just want one big primary partition. As per paqman's post above, you only need to use extended partitions when you need more than four partitions - for example, my Dell came with three partitions already (Windows boot, Windows Recovery, and Windows OS) so I shrank the Windows OS partition and used the space to create an extended partition. Inside the the extended partition I have various logical partitions for root, swap and /home for various Ubuntu releases etc. If you are interested wikipedia explains it further:
[http://en.wikipedia.org/wiki/Partition_table](http://en.wikipedia.org/wiki/Partition_table)

Great answer mikechant.

Depending on the type of Data to be stored maybe you want to consider encrypting the harddrive.

Further Reading:

[http://en.wikipedia.org/wiki/TrueCrypt](http://en.wikipedia.org/wiki/TrueCrypt)

[http://www.truecrypt.org/](http://www.truecrypt.org/)

---

### Post by northwestuntu on 2009-11-16
thanks for the great info guys :popcorn:

---

