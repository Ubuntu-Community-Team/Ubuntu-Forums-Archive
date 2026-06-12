---
title: "External Maxtor 1TB dead?!?"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by rogasgr on 2009-02-25
hello, i m new to linux and as i had some friends in university i remember them telling me they had disk recoveries made in linux. 

now a friend of mine brought me an external maxtor 1tb which fell off the desk (1meter) and seems to be dead. in windows its invisible, in linux too, although i run the ```
sudo fdisk -l
```   and i can see only my 4 other internal disks.

```
rogas@rogas-desktop:/$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x622d1191

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      484521   244198552+  42  SFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23ed23ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4660    37431418+  83  Linux
/dev/sdb2            4661        4865     1646662+   5  Extended
/dev/sdb5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xadf66efc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9729    78148161   42  SFS

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8b8bff7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        9729    78148161    7  HPFS/NTFS
```


is there anything i can do? the drive is full of great music collection and live concerts! :mad:

i promise i ll send some dvd's of the data if restored  :lolflag: (worldwide)
thks anyway  ):P

---

### Post by sloggerkhan on 2009-02-25
Dropping a drive often physically breaks internal components such as drive heads/arms. You will most likely be unable to recover and need to replace under warranty.

---

### Post by rogasgr on 2009-02-25
> **sloggerkhan said:**
> Dropping a drive often physically breaks internal components such as drive heads/arms. You will most likely be unable to recover and need to replace under warranty.

:sad::sad: so as soon as i dont see the drive in fdisk there is nothing to try more?

---

### Post by rgb96 on 2009-02-25
> **sloggerkhan said:**
> Dropping a drive often physically breaks internal components such as drive heads/arms. You will most likely be unable to recover and need to replace under warranty.

He's probably correct, however, if the data on the drive is valuable enough to you, you can probably pay someone to recover the data for you.

---

### Post by mikechant on 2009-02-25
Does it have a power light? Does this come on? Does it make any noise at all? If it's not dead, you should be able to hear it 'revving up' when first powered on.
If it's clearly not powering up at all, and you're not prepared to pay for data recovery, you might as well open it up and see if there's anything obvious - e.g. there's a slight chance the fall might have just dislodged a cable internally. If it was powered off when it hit the ground, the disc heads should have 'parked' and might have survived.

But the odds are it's probably unrecoverable unless you're prepared to pay or you've got a friendly uber-nerd handy.

---

### Post by Flyingjester on 2009-02-25
Dead mate. It's gone.

---

### Post by rogasgr on 2009-02-25
> **mikechant said:**
> Does it have a power light? Does this come on? Does it make any noise at all? If it's not dead, you should be able to hear it 'revving up' when first powered on.
If it's clearly not powering up at all, and you're not prepared to pay for data recovery, you might as well open it up and see if there's anything obvious - e.g. there's a slight chance the fall might have just dislodged a cable internally. If it was powered off when it hit the ground, the disc heads should have 'parked' and might have survived.

But the odds are it's probably unrecoverable unless you're prepared to pay or you've got a friendly uber-nerd handy.

it s power light is on but i cant hear any spin, dunno actualy how it sounds but no, no spining :mad: it does a sound  as i put it on my  eaaar. ouch its dead sure... 

i would open it but my friend is in Cuba now i have to w8 him to come back grrrr. anyway thx guys :guitar:

---

### Post by rustutzman on 2009-02-25
Depending on how important the data is you can try a couple of things. If it's not spinning, you should be able to feel the gyroscopic forces if you gently tilt it while powered up, you could buy an identical drive and replace the electronics on the outside of the drive. It's pretty easy to do. If that doesn't work you put the new one back together and use it.

Another is to place it in the freezer for about 10 minutes and then try it. Don't leave it to long though because if moisture condenses on it, it will fry when you power it up.

Russ

---

