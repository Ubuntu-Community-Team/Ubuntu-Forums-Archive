---
title: "RAID 0 - Law of Diminishing Retuns?"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2011-05-17
Hi! I am looking into taking advantage of RAID 0. My idea is to use RAID 0 over four 1TB or 2TB drives. I know that using two drives in RAID 0 provides double the speed of one drive, but will four drives give me four times the performance? I've also been looking at RAID 1+0 or RAID 5, however I am not concerned with redundancy, I am looking for maximum performance. Is RAID 0 still the best option with more than two drives?

Thanks in advance!

---

### Post by YesWeCan on 2011-05-17
Interesting question. I dont suppose anyone has plotted a graph of speed vs number of drives in RAID0. I suppose at some point the software overheads of mdadm will start to become an issue. I suspect that 4 drives will still be a gain over any fewer. RAID10 and 5 are just striping with additional overheads so should not be able to compete on speed.

---

### Post by MartyBuntu on 2011-05-17
> **pi.boy.travis said:**
> I am looking for maximum performance.

You need an SSD drive. Forget RAID 0.

---

### Post by pi.boy.travis on 2011-05-17
I've done a bit more Google, and it looks like the performance gains remain pretty consistent so long as the CPU and SATA controller can keep up. Now, for my next question. I know that I want to have a stripe size of 128kb. This will give me a compromise between smaller and larger files with a slight bias toward larger files, and a good balance between sequential and random access. My only problem is that I don't know how to tell the Ubuntu alternate installer what stripe size to use! I never asks, so I assume it either calculates some optimum number based on disk size, or simply uses some default value. How can I control which stripe size the installer uses?

---

### Post by pi.boy.travis on 2011-05-17
> **MartyBuntu said:**
> You need an SSD drive. Forget RAID 0.

I have been looking at SSDs as well, but from what I have read they have a shorter life than HDDs. However I am also considering using a RAID 0 array of SSDs and backing up to a RAID 1 array of HDDs.

---

### Post by YesWeCan on 2011-05-17
I dont know about the installer. You could always use a live CD to build the array manually and install from there. Not as slick as using the installer, tho.

---

### Post by pi.boy.travis on 2011-05-17
> **YesWeCan said:**
> I dont know about the installer. You could always use a live CD to build the array manually and install from there. Not as slick as using the installer, tho.

Genius. I never would have thought of that, I forgot palimpsest can make RAID arrays. Thanks!

---

### Post by jtarin on 2011-05-17
[Here's something to add to the mix.]("http://www.petermoulding.com/ubuntu_10.10_desktop_raid_5")

---

