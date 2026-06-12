---
title: "how to find UUID information for a 2nd disk"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by Cafargo on 2011-03-31
Hello All.

I would like to mount my 2nd disk. However, the blkid cmd returns information for my 1st disk with the swap partition (e.g. for sda1 & sda5). I checked /dev and I believe the possible other dev could be sdb. When I looked in the sdb properties there is information there indicating a 4gig volume, which would be my other disk. How do I obtain the UUID number and related information for me to add to fstab and eventually mount my 2nd disk? 
Any help would be appreciated.

Many thanks,
Cafargo

---

### Post by Morbius1 on 2011-03-31
```
sudo blkid -c /dev/null
```

blkid invoked in this manner clears the cache that blkid contains and gives you a new view of the partitions.

---

### Post by Cafargo on 2011-03-31
Hi Morbius1

I tried the new blkid cmd, but still the same two lines for sda1 and sda5 (swap) return. So, I wonder what do to next?

---

### Post by Cafargo on 2011-03-31
Newsflash: I decided to install Gparted. Ran Gparted, and discovered that my 2nd disk was listed but not partitioned. Aha! So, I created a new table and partition for sdb1, and the rest is history.

Many thanks Morbius for your help! :)

Regards,
Cafargo

---

### Post by The Cog on 2011-03-31
Ah, it all makes sense now. 

In Thread Tools at the top, you can mark a thread solved.

---

