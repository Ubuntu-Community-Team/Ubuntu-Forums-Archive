---
title: "Automatic mount of external drives"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by zebsdad on 2009-06-17
I have 4 external drives always attached to my computer. None of these drives automatically mount when I boot into ubunto 9.04. 

If I unplug one of the drives(all USB), two of the flash drives are mounted. The other flash drive and the USB (4 logical partitions) hard drive do not.

The flash drives are all fat32 and the partitions on the hard drive are NTFS.

I have one internal HDD(NTFS, Win XPSP3) that does automatically mount at boot time.

I have a screen shot of the errors I get on the drives that do not mount. (attached)

I have been reading for several days and still have not figured this out. The problem seems to be that even though it says absolute beginner talk, answers very quickly get into advanced use of tools that are certainly not self explanatory.

Please remember I have been into Linux for less than 2 weeks. Mercy to the helpless. I do have a lot of experience with windows but it doesn't seem to help much here.

Can some one help me get this done so I can go on to the next learning phase of ubunto?

---

### Post by Bodsda on 2009-06-17
> **zebsdad said:**
> I have 4 external drives always attached to my computer. None of these drives automatically mount when I boot into ubunto 9.04. 

If I unplug one of the drives(all USB), two of the flash drives are mounted. The other flash drive and the USB (4 logical partitions) hard drive do not.

The flash drives are all fat32 and the partitions on the hard drive are NTFS.

I have one internal HDD(NTFS, Win XPSP3) that does automatically mount at boot time.

I have a screen shot of the errors I get on the drives that do not mount. (attached)

I have been reading for several days and still have not figured this out. The problem seems to be that even though it says absolute beginner talk, answers very quickly get into advanced use of tools that are certainly not self explanatory.

Please remember I have been into Linux for less than 2 weeks. Mercy to the helpless. I do have a lot of experience with windows but it doesn't seem to help much here.

Can some one help me get this done so I can go on to the next learning phase of ubunto?


Hi, on the screenshot there is a 'Details >' button that contains extra information, could you please expand it and tell us what it says, print screen or copy paste, doesn't matter.

Regards,

Bodsda

---

### Post by PureLoneWolf on 2009-06-17
One thing I always recommend to new users is to run a terminal and perform sudo apt-get install pysdm

This will give you a Storage Device Manager icon inside the Administration menu.

The gui is very straightforward to use and will write to your fstab for permanent mounting.

Hope that helps

---

### Post by billgoldberg on 2009-06-17
> **PureLoneWolf said:**
> One thing I always recommend to new users is to run a terminal and perform sudo apt-get install pysdm

This will give you a Storage Device Manager icon inside the Administration menu.

The gui is very straightforward to use and will write to your fstab for permanent mounting.

Hope that helps

Didn't know about that, I always edit fstab manually.

Well, those days are over.

---

### Post by scrooge_74 on 2009-06-17
This is a good day, I learned something new 

Thanks :D

---

### Post by zebsdad on 2009-06-17
> **Bodsda said:**
> Hi, on the screenshot there is a 'Details >' button that contains extra information, could you please expand it and tell us what it says, print screen or copy paste, doesn't matter.

Regards,

Bodsda

The only errors are written in the two lines of the attachment. Like libhal.c:1399, etc..

---

### Post by zebsdad on 2009-06-17
> **PureLoneWolf said:**
> One thing I always recommend to new users is to run a terminal and perform sudo apt-get install pysdm

This will give you a Storage Device Manager icon inside the Administration menu.

The gui is very straightforward to use and will write to your fstab for permanent mounting.

Hope that helps

I installed the Storage Device Manager and it seems to be work for mounting right now but it does not automount at startup. 

If i unplug and replug my flash drive called "Money" I get an error that says "you are not privileged to mount Money".

---

