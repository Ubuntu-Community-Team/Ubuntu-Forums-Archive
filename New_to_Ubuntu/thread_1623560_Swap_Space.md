---
title: "Swap Space"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by kroq-gar78 on 2010-11-16
Hello Ubuntu Community,

I have read about swap space after I installed ubuntu and set it to 244 MB.  I read that swap space shuold be about 1.5 times that of my RAM (I have 3GB) and think I should add more swap. Can I just boot into live cd and use gparted to resize my swap space? I would rather not have a file that is 4GB large on my system and instead have a parition dedicated to swap on my permanent external drive (320GB).

Can I just resize my swap partition or do I have to create a 4GB file and add it as swap?

Thanks in advance.

---

### Post by drs305 on 2010-11-16
Yes, you can just expand the partition.  It probably doesn't need to be 4GB but if you have the space to spare that's ok.

Afterwards just check the fstab and partition UUIDs to make sure they are still the same:
```
sudo blkid -c /dev/null | grep "swap" && grep "swap" /etc/fstab
```

---

### Post by kroq-gar78 on 2010-11-20
yay finally did it and it works! now running w/ 3GB or ram :D

thanks

---

### Post by beew on 2010-11-20
Actually I don't understand what is the point to the 1.5Xram rule as Linux hardly uses any swap. I read that this is intentional because it is a lot faster to use ram and that maxing it out is no problem because ram is there to be used swap is only needed infrequently to get you out of temporary memory jam so the pc wouldn't freeze up instead. My pc rarely uses more than 12~ 15% of swap and never to my knowledge uses more than 20%. So I would think it is a waste of disk space to have a few G of swap which Linux would never use anyway.

---

### Post by drs305 on 2010-11-21
@ beew,

I believe the issue is when hibernating but I only know what I've seen on these forums...

---

### Post by drs305 on 2010-11-21
@ beew,

I believe the issue is when suspending/hibernating but I only know what I've seen on these forums...

---

