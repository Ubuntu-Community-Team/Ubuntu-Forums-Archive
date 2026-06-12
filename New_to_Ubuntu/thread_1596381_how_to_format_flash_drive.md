---
title: "how to format flash drive?"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by jonnny_j22 on 2010-10-14
okay, so I did a dumb thing, I was deleting partitions for a new layout and forgot my flash drive was attatched. I accidentally deleted all partitions on the pen drive and now ubuntu doesn't recognise it when I connect it. How do i format it so it will work again?

---

### Post by migs73 on 2010-10-14
Try using the Disc Utility in System > Administration.
If it sees the drive it will allow formatting and partitioning.

---

### Post by jonnny_j22 on 2010-10-14
sorry I don't seem to have disk utilities installed?

---

### Post by cjv8888 on 2010-10-14
Can you see the flash drive in Administration/Gparted?

---

### Post by zaphod777 on 2010-10-14
I also believe that you can right click and select format.

---

### Post by migs73 on 2010-10-14
> **zaphod777 said:**
> I also believe that you can right click and select format.

I believe the OP wants to repartition also.

I assume you are not using 10.10, in which case Gparted (no longer in 10.10?) will do the same job as previously stated by cvj888.

---

### Post by zaphod777 on 2010-10-14
> **migs73 said:**
> I believe the OP wants to repartition also.

I assume you are not using 10.10, in which case Gparted (no longer in 10.10?) will do the same job as previously stated by cvj888.

I see. I don't think gparted was every included on the install just on the liveCD desktop. I have always had to install it afterwards.

---

### Post by cjv8888 on 2010-10-14
ok

```
sudo apt-get install gparted
```

---

### Post by cgroza on 2010-10-14
Gparted is the right way to go. Make sure you select the flash drive from the menu.

---

### Post by cascade9 on 2010-10-14
Gparted is probably the easiest way, but there are lots of others.

---

### Post by jjex22 on 2010-10-14
or gparted live cd?

---

### Post by migs73 on 2010-10-14
Glad to be of help, even although nothing I mentioned was any use:lol::roll:


Edit; this is a response to the post below! I am sure it was above mine a minute ago? How'd I manage that then :confused:

---

### Post by jonnny_j22 on 2010-10-14
Cheers guys! running gparted didn't detect the drive, but your advice  did remind me that I had gparted live cd somewhere about and a bit of a  rummage and I was able to format the drive from the live cd!:smile:

---

