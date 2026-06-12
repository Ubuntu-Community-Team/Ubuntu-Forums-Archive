---
title: "Adding a second internal hard drive"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by LordBenjamen on 2009-07-29
I'm kinda a noob to linux but i'm really starting to love it.. i've already filled my 250g hard drive up and i've been trying to add another 250g hd from my old computer.. I've managed to get gparted and format the drive.. its unallocated but i can't figure out how to get it so i can use it.. if someone can help me i'd be very grateful.. thanks.. i'm not very good with ubuntu so i might need a some deep explaining..

---

### Post by Lavaeagle on 2009-07-29
I installed my internal HDD under Vista and formatted it to NTFS so I would suggest:
- When you format it make sure that it formats to ext3 (This is what Ubuntu reads off of)

---

### Post by gletob on 2009-07-29
In Gparted right click the unlocated space in the list and click new.  Then in The box that says filesystem choose witch FS to go with.

EXT3/4 (I perfer 4, but it depends on what version your running) or NTFS if you want to share the drive with windows.

What did you have in mind for this drive?

---

### Post by LordBenjamen on 2009-07-29
I just want the space for media.. movies, music, etc.. but the problem is when i format into ext3/4 i still can't put any media into the drive

---

### Post by whitethorn on 2009-07-29
do you know if it's getting mounted? Or what kind of error are you getting?

Could you paste the output of 

```

sudo fdisk -l

```
and
```

df -h

```

---

