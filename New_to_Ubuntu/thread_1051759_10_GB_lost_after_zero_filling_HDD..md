---
title: "10 GB lost after zero filling HDD."
date: 2009-01-27
forum: New to Ubuntu
---

### Post by sadicote on 2009-01-27
I had Windows XP  with which i had partitioned my 160 GB hard drive, installed it on 10 GB and then installed Ubuntu over it. Because of some problems with my Nvidia drivers, and after gaining enough confidence with Ubuntu Ibex, i decided to zero fill my Hdd with my Seagate tools for DOS and reinstall Ubuntu. After the 'full erase' operation my 160 GB Hard disk showed capacity as only 150 GB. How can i recover my HDD max. native capacity? 

Also, now the partitions that i made with Windows XP are also inaccessible to me after deleting XP from it, as seen from the screenshots, even though i reformatted them using Gparted. I am willing to backup and reinstall, if that is what it takes.:)

---

### Post by halovivek on 2009-01-27
The Linux swap partition is still exists in your hard disk. The picture which you have posted is telling.

---

### Post by sadicote on 2009-01-27
That's part 2 of the problem (ie. post-installation), even so how to make this available as free space for storage.

---

### Post by halovivek on 2009-01-27
If you are not using the Linux anyway. In windows- my computer- manage- disk storage . Right click on that 10GB and delete the partition. If you want to use that in Linux. Create a swap file instead of SWAP partition and you can use that one.

---

### Post by bgerlich on 2009-01-27
The 10Gb is not lost. The drive manufacturer states the driver size in gb as in 1000 Mb. The partitioning tool shows size as it is supposed to be gb = 1024 mb , thus the diffrence

---

### Post by sadicote on 2009-01-27
> **bgerlich said:**
> The 10Gb is not lost. The drive manufacturer states the driver size in gb as in 1000 Mb. The partitioning tool shows size as it is supposed to be gb = 1024 mb , thus the diffrence
No, i don't think that's it, coz i had my capacity listed as 160.042 GB. And i have used zero fill before. It was only after erasing this dual boot system that i had this shortfall. Also when i try to set capacity to max. native, i get an error message, with "could not set capacity to max. native"

---

### Post by halovivek on 2009-01-27
Could you post what is the operating system version of the system?
is it 32 bit or 64 bit. since 32 bit have limitation showing the higher data size.

---

### Post by sadicote on 2009-01-27
32 bit, i386 version

---

### Post by talsemgeest on 2009-01-27
> **sadicote said:**
> 32 bit, i386 version
...of which version of windows?

---

### Post by hyper_ch on 2009-01-27
> **bgerlich said:**
> The 10Gb is not lost. The drive manufacturer states the driver size in gb as in 1000 Mb. The partitioning tool shows size as it is supposed to be gb = 1024 mb , thus the diffrence

I agree here

hd manufacturers use 1000 and not 1024. So 160 GB = 160'000'000'000 bytes.

However 160'000'000'000 bytes = 156'250'000 kb = 152'587.89 mb = 149.01 gb.

---

### Post by mcduck on 2009-01-27
I don't really see any problem there.

9,77GiB + 3GiB + 34,53GiB + 1,52GiB + 100,22GiB = 149,04GiB (160,03GB)

And the disk itself is 149,05GiB (160,04GB)

---

### Post by halovivek on 2009-01-27
> **hyper_ch said:**
> I agree here

hd manufacturers use 1000 and not 1024. So 160 GB = 160'000'000'000 bytes.

However 160'000'000'000 bytes = 156'250'000 kb = 152'587.89 mb = 149.01 gb.

I agree with this.

---

### Post by Roadbloc on 2009-01-27
This may not be much help by try [http://partitionlogic.org.uk/](http://partitionlogic.org.uk/)


;)

---

### Post by sadicote on 2009-01-27
I am comforted by your arithmetic, that's the exact figure, but i am telling the truth when i say that after an earlier zero-fill my capacity was displayed as 160.042 GB (by the Seagate tools for DOS), it was only after using it when i had this dual-boot 'WindowsXP and Ubuntu Ibex' system that this happened--and all you are trying to do is help--i am disgusted with myself!

---

### Post by talsemgeest on 2009-01-27
So the seagate tools now say 150GB? Or are you using a different program, because different porgrams count it differently.

---

### Post by sadicote on 2009-01-27
> **Roadbloc said:**
> This may not be much help by try [http://partitionlogic.org.uk/](http://partitionlogic.org.uk/)


;)

Looks very promising..just downloaded it..will update here, later.

---

### Post by sadicote on 2009-01-27
> **talsemgeest said:**
> So the seagate tools now say 150GB? Or are you using a different program, because different porgrams count it differently.

So it doth say, the very same Seagate tool :)

---

### Post by sadicote on 2009-01-29
This is the output of 'sudo fdisk -l: 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x556b556b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10241406   83  Linux
/dev/sda2            1276        6374    40957717+   f  W95 Ext'd (LBA)
/dev/sda3            6375       19457   105089197+  83  Linux
/dev/sda5            1276        1667     3148708+   7  HPFS/NTFS
/dev/sda6            1668        6175    36210478+  83  Linux
/dev/sda7            6176        6374     1598436   82  Linux swap / Solaris
sade@sade-desktop:~$ 

My problem is how to make /dev/sda3 available for storage. I followed the posts on HDD partitioning, etc. but i still don't get it; what can i say, i am a moron, but i am committed to Ubuntu.:D

---

