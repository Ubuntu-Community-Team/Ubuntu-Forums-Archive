---
title: "Resize partition question"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by mawil1013 on 2010-05-20
OK, I'm about to shrink my vista's c: partition by 40,000 MB.

What I see is,

Volume          C: Cap. 222.03GB, Free 149.54GB, %Free67
Volume Recovery D: Cap. 10.85GB,  Free 1.70GB,   %Free16

On the Shrink C: after changing I see,

Total Before 227357
Available    59414
Amount/Shrink 40000
Total After  187357

Now my question is about the 'Available' amount of 59414, I see Free 149.54GB, shouldn't 'Available be more like 109.54GB after shrink of 40GB???

regards,
piedmont

---

### Post by nhasian on 2010-05-20
it sounds like your trying to shrink the volume from inside of Vista's Disk Management right?  that's a pain in the butt and doesn't allow you to shrink the volume as much as you'd like to.  instead I recommend booting from an ubuntu live cd and resizing the partition from System->Administration->Gparted.

I know a lot of people are going to post after me saying how you should shrink the NTFS volume using windows tools and not gparted - and if it actually WORKED i'd recommend that method too.  But it has never worked for me.  On the other hand, i've used gparted many times on many different machines to shrink NTFS partitions and i've never had any issues.  of course to be on the safe side, always backup first.

---

### Post by mawil1013 on 2010-05-20
> **nhasian said:**
> it sounds like your trying to shrink the volume from inside of Vista's Disk Management right?  that's a pain in the butt and doesn't allow you to shrink the volume as much as you'd like to.  instead I recommend booting from an ubuntu live cd and resizing the partition from System->Administration->Gparted.

I know a lot of people are going to post after me saying how you should shrink the NTFS volume using windows tools and not gparted - and if it actually WORKED i'd recommend that method too.  But it has never worked for me.  On the other hand, i've used gparted many times on many different machines to shrink NTFS partitions and i've never had any issues.  of course to be on the safe side, always backup first.

i found and installed ubuntu using wubi, case closed.

---

### Post by nhasian on 2010-05-20
great.  don't forget to mark your threat solved.

---

