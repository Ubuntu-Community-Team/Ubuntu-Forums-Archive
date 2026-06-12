---
title: "reformating hard drive"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by dsos30 on 2011-06-03
Hi everyone,

If I am using ubuntu through windows 7, & I only want to use ubuntu on my laptop, would I have to reformat my hard drive first then put my ubuntu CD in, and restart my laptop & go through the installation from there?

Hope my question makes sence.. 

Many thanks dsos30 newbie......

---

### Post by fatality_uk on 2011-06-03
Do you have Ubuntu installed through WUBI at the moment?

---

### Post by LowSky on 2011-06-03
If you installed Ubuntu using Wubi then yes... if you installed them side by side, then all you need to do is install gparted, delete the windows 7 partition, and then increse the size of the ubuntu partition.

---

### Post by dsos30 on 2011-06-03
Hi Guys,

No I'm not using Wubi I am using the "try it first section" for the full version of ubuntu 11.04....

Thanks...

---

### Post by frogo on 2011-06-03
> **dsos30 said:**
> Hi Guys,

No I'm not using Wubi I am using the "try it first section" for the full version of ubuntu 11.04....

Thanks...

Hi, I did two installs this way (USB) and --- warning --- that's the extent of my experience. 

The first time I kept a factory install of Windows around and had a dual boot. On the second install I didn't bother with dual boot and installed only Ubuntu. 

When you install with the USB installer, there comes a moment when you have to select your partition information. 

For dual boot you have to reserve some space for the existing OS, you can choose to have more partition and so on. The details of this escape me and I think I followed some 101 how to found most likely on the ubuntu documnetation site. 

If you want to just install Ubuntu over whatever exist, there's an option (which roughly amounts to ticking a box) and that allocates the needed partitions (2 in my case: ubuntu + swap). 

In short, for all I understand, you don't have to worry about formatting prior the install. 

hope this helps

---

### Post by ajgreeny on 2011-06-03
So I presume you have an icon called "Install Ubuntu" on your desktop or in the launcher on the left hand side of the screen;  I can not get unity to run so I am not sure where it is in that desktop layout.

If you do have that icon you can just click on it in the launcher, or double click if on then desktop, and the install dialog will appear.

If you have Vista or Win7 I recommend you shrink the windows OS partition using its own disk management utility, and after defragging at least twice, to give some free space for ubuntu, then run the live CD as you have at the moment, and go through the installation, choosing the manual partitioning "Something else" on the partitioning page, where you will see the options for how to install.

Exactly how you go about it will depend on the partition layout of your current disk(s), so let's see the output of ```
sudo fdisk -l
``` in the live ubuntu CD terminal, please.

If you want to get rid of windows then see the info at [Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome")

---

