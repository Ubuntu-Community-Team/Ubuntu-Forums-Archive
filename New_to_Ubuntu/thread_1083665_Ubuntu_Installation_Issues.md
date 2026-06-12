---
title: "Ubuntu Installation Issues"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by GrimmReaperVI on 2009-03-01
I think something's wrong my my Ubuntu CD (8.1 downlaoded and burned) I'm trying to install Ubuntu on my new PC. I have freed about 100GB for ubuntu. 
I fire up the installer. When it askes where to install, I choose "Guided - Use largest continuous free space" But in the Before and After screen I get this:

Before:

(__WINDOWS_PARTITION_)(___FREE_SPACE__)

After:

(________UBUNTU PARTITION_____________)

Which is teh same screen I get with "Use entire disk"!!
I've tried to "Resize Windows Partition and use freed space". This option looks ok but Ubuntu just resizes the windows parition and doesn't install! Help?

---

### Post by feelshift on 2009-03-01
Just use Manual Partitioning. Make a small swap partition (about 1 GB) and a ext3 one where you will install Ubuntu. :popcorn:

---

### Post by Kevbert on 2009-03-01
Select manual partitioning. In the 100Gb free space make a linux swap partition of twice your RAM. Make the rest formatted ext3 and mount point / for the system.

---

### Post by GrimmReaperVI on 2009-03-01
It's fine If I leave 0% free space?

---

### Post by philinux on 2009-03-01
Create these
```
mount point
/           12 gig
swap        twice ram 
/home       rest of space
```

---

### Post by presence1960 on 2009-03-01
by "free space" I assume you mean unallocated space. That will be fine as your Ubuntu install will take less than 4Gb on the / partition. You will have the rest "free" on the / partition.

---

### Post by presence1960 on 2009-03-01
> **philinux said:**
> Create these
```
mount point
/           12 gig
swap        twice ram 
/home       rest of space
```

+1

I use a separate home partition. There seems to be 2 schools of thought on the benefits of a separate home partition. I prefer to have one. But as with everything else it is about your preference.

---

### Post by GrimmReaperVI on 2009-03-01
> **Kevbert said:**
> Select manual partitioning. In the 100Gb free space make a linux swap partition of twice your RAM. Make the rest formatted ext3 and mount point / for the system.

I used this method, left with nill free space. Everything works (for now). 

Which boot option for Vista do I use?

I have 2 the same XD

---

