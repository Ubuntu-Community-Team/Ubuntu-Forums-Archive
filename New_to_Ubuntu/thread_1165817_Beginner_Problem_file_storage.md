---
title: "Beginner Problem file storage"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by Psydan on 2009-05-21
So I just installed Ubuntu, as a dual-boot with Vista (for games), and whenever I try to do anything, like update, or save a file, or download a Firefox add-on, it tells me there is no memory, and that I should take action to free up memory. I have over 150G of free space on my hard drive, though, partitioned for ubuntu, I just can't figure this out. Any suggestions? I'm running on an HP laptop, a couple years old, I don't think it's a hardware problem, and if I boot Windows I have no problems.

---

### Post by Zzl1xndd on 2009-05-21
If its saying your out of Memory that is normally referring to RAM not Hard drive space.

---

### Post by Psydan on 2009-05-21
The error comes up as
Not enough free disk space
The upgrade needs a total of 110M free space on disk '/'. Please free at least an additional 110M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

---

### Post by GXice on 2009-05-21
You may have it partitioned, but is it correctly mounted?

I had this problem in the past, unless you specifically edit the fstab.conf file the system won't mount the drive automatically.

---

### Post by Zzl1xndd on 2009-05-21
When partition to install Ubuntu how much space did you give it? Also it might be worth going to Applications > Disk Usage Analyzer this should display a line with your total file system capacity and how much is used.

---

### Post by bacardiandwatermelon on 2009-05-21
Alot of people have got caught out with the installer and didn't move the slider when selecting their partition size. As a result only partitioned the minimum size which is like 2.3G or something..

---

### Post by Psydan on 2009-05-21
I'm not sure what the problem is, I gave it 150GB to begin with, after realising there was a slider there, but I partitioned it on my external hard drive, is that a problem?

---

### Post by oldos2er on 2009-05-21
Can you run this in a terminal, and post the output here?
```
sudo fdisk -l
```

---

