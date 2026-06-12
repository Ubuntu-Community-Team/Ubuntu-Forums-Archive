---
title: "how big of a solid state drive do I need for ubuntu?"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-06-05
Hi Community:

My machine is 7 years old and I'm thinking of building a new machine with a solid state drive for the Ubuntu operating system.

How big must the solid state drive be?

Thanks!
Phil Smith
Duluth, GA

---

### Post by mikewhatever on 2011-06-05
Obviously, the more size the better, but the comfortable minimum, to make sure you don't instantly run out of space, is about 8-10GB.

---

### Post by Matt__ on 2011-06-05
My dell netbook has an 8Gb SSD, just 3.5Gb of that is Ubuntu OS(10.04) + added software, 1Gb of files and the rest spare +swap. all other files are on external HDD or network.

So say 5Gb would be the absolute bare minimum, 8Gb at least in practical terms, and anything more is a bonus. so like Mike says :)


try here [Best Buy](http://stores.bestbuy.com/504/details/), theyre supposed to be cheap.
or a [60GB corsair](http://www.ncixus.com/products/?sku=61604&vpn=CSSD-F60GB2%2FRF2&manufacture=Corsair&promoid=1343) for $70 sounds a good price to me.(refurb drive)

---

### Post by terrykiwi83 on 2011-06-05
My system has a 64GB SSD which is used just for the Linux OS, I also have 1TB & 620GB SATA 2 Drives for storage and that setup works well for me.

But I personally recommend 64GB as Min.

---

### Post by Mr. Shannon on 2011-06-05
If you are talking about putting the root file system on the drive and putting /home somewhere else then you could get by with 20-25GB.  I have a lot of software installed on a 19GB partition and I have just enough room for a temporary DVD ISO file.

---

### Post by oldfred on 2011-06-05
I recommend 20-25GB for / including a bare bones /home where your data then is one another partition/drive. Then all the boot files & user configuration files that are accessed most often are on the root partition. 

My /home without any data is only about 250MB of hidden files & folders. I do move some data files like Firefox & Thunderbird profiles out of /home also even though they are hidden folders in /home.

They suggest gpt not MBR and only 25% normal use with a 7GB install or about 30GB drive.
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.

---

### Post by Dondermans on 2011-06-05
Caveat emptor! It is not uncommon -or so I have read- for lower capacity models to suffer from sub par performance when compared to higher capacity ones.

Also, it appears to be quite difficult to permanently erase data from SSDs (see message [_#12_]("http://ubuntuforums.org/showpost.php?p=10905832&postcount=12") in the thread [_Securely delete data from Flash Drive_]("http://ubuntuforums.org/showthread.php?t=1656974")).

---

### Post by wolfen69 on 2011-06-05
Since your root install will probably never go over 15gb, you could get away with using a 64gb ssd and put /home on it also. But you'll have to monitor how much you save on it, or just keep all your stuff on a separate drive.

---

