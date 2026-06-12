---
title: "Keep Trying or Not!"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by Justin1996 on 2010-02-03
I see where other have used this laptop and succeded but,I can't decide whether or not to keep trying to install Ubuntu on my Dell Inspiron 6000 Laptop. I have tried that and a few other version of Linux and the same thing is happening on every one. It installs and look great from what I can see and do, but locks up as soon as I try to use any of the programs. Wired and wireless works great, I can even tether it to my Samsung Jack and use ICS fune. But if I open Firefox or try to get updates or even try and change the background it will work for a minute or two and lock up with nothing working and no hotkey combonations will change that. It won't run long enough to make any changes to the system or add packeges so I'm at a lose. Below is a run down of what my system is running and any help would be greatly appreciated. 
 
 
Dell Inspiron 6000
 
Dual booted w/Windows 7 (which runs great) 
Bios A09
2.0GHz Intel Pentium M
2 GB ram
120 GB HD
ATI X300 Video

---

### Post by Tholley on 2010-02-03
If you are dual booting, maybe you are not allowing enough space for Ubuntu to operate? 
 
What version of Ubuntu have you tried to install, and what process are you doing to install it?

---

### Post by Justin1996 on 2010-02-04
I gave the partition a size of 50 gigabytes, so I would assume that would more than be enough. I have let windows make the partiton, used a third party partitioning program and let ubuntu make it's own with the results being the same. It must be something small I'm overlooking with all the people useing the same laptop and not having any troubles.

---

### Post by audiomick on 2010-02-04
50 GB should be ample. I have, however, heard of the installer only making a tiny partition for some odd reason. So that we can see what is going on a bit, can you post the ouput of
```
sudo fdisk -l
```that is a lower case L, not a figure one.
as well as the first block of text from
```
top
```

That will list your partition table (fdisk) and what is happening with your RAM (top).

---

### Post by LowSky on 2010-02-04
Did you install ubuntu using WUBI?

---

### Post by Justin1996 on 2010-02-04
I have tried installing through windows as we'll as through the ubuntu installer. I have installed and uninstalled, deleted partitions and made new partitions around 10 times, downloaded ubuntu 5-6 times and it's always the same. I have tried different size partitions from 20 gig to 50 and more. I get just enought aste to be interested and  "WHAM" locks up. I would think it's hardware based if it were not for the fact that Windows 7 run so great.  Thanks again for your help.

---

### Post by Justin1996 on 2010-02-04
I will have to go and re-install it and give you that info. I deleted it no use to take up the disk space on something I don't use. So I was hoping to try something new on the next install.

---

### Post by Justin1996 on 2010-02-04
> **audiomick said:**
> 50 GB should be ample. I have, however, heard of the installer only making a tiny partition for some odd reason. So that we can see what is going on a bit, can you post the ouput of
```
sudo fdisk -l
```that is a lower case L, not a figure one.
as well as the first block of text from
```
top
```
 
That will list your partition table (fdisk) and what is happening with your RAM (top).
I will have to go and re-install it and give you that info. I deleted it no use to take up the disk space on something I don't use. So I was hoping to try something new on the next install. 
 
 
Forgot to check the box.

---

### Post by Justin1996 on 2010-02-06
> **audiomick said:**
> 50 GB should be ample. I have, however, heard of the installer only making a tiny partition for some odd reason. So that we can see what is going on a bit, can you post the ouput of
```
sudo fdisk -l
```that is a lower case L, not a figure one.
as well as the first block of text from
```
top
```That will list your partition table (fdisk) and what is happening with your RAM (top).



I think this is what you are looking for. I hope.

---

### Post by cwalker1960 on 2010-02-06
swap file, swap partition,    you're using up all your resources. linux needs a place to dump unused resources

---

### Post by dolphinaura on 2010-02-06
Have you tried the dell ubuntu isos?
their avalible here.[http://linux.dell.com/files/ubuntu](http://linux.dell.com/files/ubuntu)

You will have to build manually isos for karmic, but you can just use the jaunty isos and see if it works.

If it works, post back and ill make the effort of generating a karmic DVD for ya.

---

### Post by Justin1996 on 2010-02-08
> **cwalker1960 said:**
> swap file, swap partition,    you're using up all your resources. linux needs a place to dump unused resources
OK newbie here. What exactly does that mean. And I when I reloaded to get these files I put the video card on the lowest setting and everything seems to work OK are at least no lock ups so maybe a driver issue???? I dont really know.

---

