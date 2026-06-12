---
title: "Install Ubuntu on smallest partition"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by oziwombat on 2009-02-14
Hi Guy's 
New to the forum & would like to know if I can install Ubuntu on my 15gb partition of my H/Drive ?  I set up XP Pro on a 60gb partition & now Ubuntu wants the 60gb part & I want it on the 15gb part . Any idea's .:confused:
Ozi

---

### Post by adult swim on 2009-02-14
in step 4 (the partitioning part) of the install select manual and click next. it will present you with a list of the current partitions. double click the 15gb partition and choose it to be formatted to ext3 and choose / as the mount point.  then you can continue with the install as normal.
EDIT:  before you do this you will probably need to create a small partition 1-2gb to be used for swap space (kind of like windows page file)
it may be easiest to delete the partition you have created for ubuntu all together and leave it unallocated.  i believe there is an option on install to use the largest unallocated space for installation.  that way you wouldnt have to create teh swap partition

---

### Post by oziwombat on 2009-02-14
> **adult swim said:**
> in step 4 (the partitioning part) of the install select manual and click next. it will present you with a list of the current partitions. double click the 15gb partition and choose it to be formatted to ext3 and choose / as the mount point.  then you can continue with the install as normal.
EDIT:  before you do this you will probably need to create a small partition 1-2gb to be used for swap space (kind of like windows page file)
it may be easiest to delete the partition you have created for ubuntu all together and leave it unallocated.  i believe there is an option on install to use the largest unallocated space for installation.  that way you wouldnt have to create teh swap partition

Thanks & will try that .
Cheers 
Ozi

---

### Post by stalkingwolf on 2009-02-14
You should also be able to select the 15gb drive and select "use entire partition".  if you do this it will create the swap partition for you.

---

