---
title: "Extended Drive??? 164 instead of 160???"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by randolf_ambrose on 2010-05-03
here is a look at my disk status...

[IMG]http://rahulrkrishnan.0fees.net/images/Screenshot.png[/IMG]

my HDD size is 160...

I created a 4G swap...
28G ext4 for Ubuntu...
and remaining 128 fat 32 to store my main files..

now where did this Extended space of 4G came???
that'd mean 164G instead of 160G!

i'm not that good with partition and all that stuff...

is this extended 4G space the same as my Swap space???


also: how can i change myfat32 volume's label... i tried to change it with this disk utility but label change option was disabled... i guess i have to log in as admin???

---

### Post by cariboo on 2010-05-03
Did you create the fat 32 partition on an extended partition? You are aware of the file size limitation of vfat partitions, you can only store files with a maximum size under 4Gb, that means you can't store some dvd iso's on the drive. A better idea would be to wipe out the vfat partition and create an ntfs partition as a primary partition. Read/write to ntfs is quite stable, and allows you to reliably store files over 4Gb in size.

---

### Post by randolf_ambrose on 2010-05-03
> **cariboo907 said:**
> Did you create the fat 32 partition on an extended partition? You are aware of the file size limitation of vfat partitions, you can only store files with a maximum size under 4Gb, that means you can't store some dvd iso's on the drive. A better idea would be to wipe out the vfat partition and create an ntfs partition as a primary partition. Read/write to ntfs is quite stable, and allows you to reliably store files over 4Gb in size.

not sure if i created that fat32 on extended partition... was long time ago... :-D

havent tried storing 4G files... i guess i'd be in trouble... 

yea... i agree... i gotta repartition it as primary...

but i guess, i created my SWAP as extended partition!!! and that could be the 4G extended partition thats shown there!!!

---

### Post by srs5694 on 2010-05-03
Different utilities report sizes in different ways. In particular, some uses base-10 numbers (1KB = 10^3 bytes, 1MB = 10^6 bytes, 1GB = 10^9 bytes), whereas others use base-2 numbers (1KiB = 2^10 bytes, 1MiB = 2^20 bytes, 1GiB = 2^30 bytes). Note that I've used KB, MB, and GB as the base-10 abbreviations and KiB, MiB, and GiB as the base-2 abbreviations. This usage is technically correct, but uncommon; many tools use KB, MB, and GB when referring to the base-2 figures.

Typically, hard disk manufacturers use base-10 values, but these values are also not precise, so a "160GB" disk will hold *approximately* 160,000,000,000 bytes -- it could be a little less or (more likely) a little more. Disk utilities *usually* employ base-2 values, so people often end up wondering why they're getting less space than they paid for, and all sorts of incorrect explanations pop up.

Your confusion, of course, goes the other way, but I can't give a more precise answer without knowing the *precise* sizes of your disk -- and if you were to provide that information, you could find the answer yourself. I suggest you start like this:

```

sudo fdisk -lu

```

This command will display the sizes of your disks and all your partitions in sectors, each sector being 512 bytes. You can then see how all the numbers add up. Note that most disks are formatted with three types of partitions: *primary,* *extended,* and *logical.* You can have a maximum of four primary and extended partitions, but an extended partition serves as a placeholder for as many logical partitions as you like. If you've got extended and logical partitions, you'll see this in the fdisk output.

---

