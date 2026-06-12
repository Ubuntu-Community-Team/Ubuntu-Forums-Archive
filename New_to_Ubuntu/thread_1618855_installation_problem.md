---
title: "installation problem"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by Rajshekar on 2010-11-11
HI...i am a beginner to ubuntu.....
           
       problem :  1. when installing ubuntu-10.04, my other OS(xp professional) is not detected.
                        2. do i have to lose all data on my drives while installing
                        3. how much free space is required for same version installing.
                        4. i have a partitioned free drive(when in windowsXp),how to direct installation into that drive.

---

### Post by mastablasta on 2010-11-11
> **Rajshekar said:**
> HI...i am a beginner to ubuntu.....
1. when installing ubuntu-10.04, my other OS(xp professional) is not detected.

 
Can you still boot in winXP? if so then ubuntu should recognies it. can you boot ubuntu from CD and try it?
 
> 
2. do i have to lose all data on my drives while installing

No. you will be able to keep your data.
 
> 
3. how much free space is required for same version installing.

i would say about 20-30 GB is enough, though you can get away with 5-10gb i believe... 
 
> 
4. i have a partitioned free drive(when in windowsXp),how to direct installation into that drive.
 
remember to defragment before partitioning. when you partition don't from the drive. then when installing ubuntu just select largest free space and that should point it to the newly created partition.

---

### Post by Quackers on 2010-11-11
If you have made a partition specifically for Ubuntu I would delete it and leave the space as unallocated. That way the Ubuntu installer should see it and you should be offered the choice of installing to "the largest free space" on the disc.

---

### Post by theozzlives on 2010-11-11
Boot the live CD, choose try Ubuntu, and go to Applications > Accessories > Terminal. Type:
```
fdisk -l
```
(note that's a lower-case L) and copy and paste the results here.

---

### Post by Rajshekar on 2010-11-11
thank you guys a lot...am on it now trying...thank you once again

---

