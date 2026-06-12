---
title: "Question about /boot"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by mharrison on 2009-09-30
On my system, I had to do a separate partition for /boot because of a system error when booting.  It was something to do with the hard drive, but it happened a while ago and all I remember is the solution was to create a /boot partition.

My question is, now that time has passed since doing so, what should I expect as far as the possibility of /boot filling up, and if it starts to, what steps can I take to clean it up?

---

### Post by BQAggie2006 on 2009-10-01
To get a better idea of your situation, what release of Ubuntu are you running, when did you create the new /boot partition, and how big did you make?
 
It's possible that the /boot partition could fill up as kernel updates are pushed out and initrd and vmlinuz images are created. However, with the short Ubuntu support cycles (except for the LTS releases), there's probably not a high possibility of it happening. If you are worried about it, you can keep tabs on it with the following command:
```
df -h /boot
```
 
As far as clean up, I'm not sure if the update process will clear out any old kernel images if there isn't any room left or not. You can try to manually move the files for older kernel images (I say move and not remove) to another partition and then update the GRUB boot menu to remove the old kernel entries.

---

### Post by mharrison on 2009-10-01
I'm running Jaunty,  I created it around March/April.  The "documentation" I read to solve my problem said to make it 250 megs, but I made it 1 gig to have some overkill.

I've been using the command you put in to keep an eye on it from time to time, mostly after I notice kernel upgrades, but I was just curious.  Since I keep all of my data on my server, wiping the main machine is not a horrible process for me....I have a lot of settings backed up as well to make restoring easier.

---

### Post by BQAggie2006 on 2009-10-01
With a 1GB /boot partition, I don't think you have anything to worry about.

---

### Post by LewRockwell on 2009-10-01
yes, 1GB should be plenty

was the separate boot partition necessary due to an encryption issue

.

---

### Post by mharrison on 2009-10-01
> **LewRockwell said:**
> yes, 1GB should be plenty

was the separate boot partition necessary due to an encryption issue

.

No, actually it was due to a error I was getting when the system would try to boot.  I don't remember exactly what it was, but it had to do with the size of my partition and the number of heads or cylinders wasn't supported....It was strange because the system worked fine for months and then one day threw the error out of the blue.

I figured a gig should be fine, but I wanted to check because I was checking my drive usage and just got curious.

---

