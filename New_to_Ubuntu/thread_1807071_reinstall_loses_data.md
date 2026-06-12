---
title: "reinstall loses data"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by Carcharoth on 2011-07-18
We had a dual boot computer with XP and Maverick Meerkat. Windows crashed, and I needed to reinstall it. I had convinced myself that Windows would leave alone the partition that Ubuntu sat on, but I cannot seem to see that part of the hard drive now.

I tried a live USB and a live CD, but Ubuntu does not do a complete load, so I cannot browse the part of the hard drive Windows does not read.

The Windows reinstall completed, but ended up taking 150 gig out of a 160 gig drive - and I am pretty certain I told it to stay confined to the approximately half of the hard drive I gave to it in the first setup.

There was data on the Ubuntu part of the drive that was graphical artwork which my daughter created. I would hate for that to be lost, or I would just wipe it out and start over.

Any ideas? Bright ideas are preferred, but I will take a look at anything at this point.

---

### Post by mikejonesey on 2011-07-18
unfortunatley it is lost (windows formats then overwrites)... if you wish you can try to use test disk to try to restore the old partition, expect to blow up the existing windows by doing this, but you can easily write your partition table back after to fix windows again...

just make sure you grab the current config first;
```
fdisk -u -l /dev/"your hard disk code here (hda|sda)"
```

---

### Post by amjjawad on 2011-07-18
> **Carcharoth said:**
> We had a dual boot computer with XP and Maverick Meerkat. Windows crashed, and I needed to reinstall it. I had convinced myself that Windows would leave alone the partition that Ubuntu sat on, but I cannot seem to see that part of the hard drive now.

I tried a live USB and a live CD, but Ubuntu does not do a complete load, so I cannot browse the part of the hard drive Windows does not read.

The Windows reinstall completed, but ended up taking 150 gig out of a 160 gig drive - and I am pretty certain I told it to stay confined to the approximately half of the hard drive I gave to it in the first setup.

There was data on the Ubuntu part of the drive that was graphical artwork which my daughter created. I would hate for that to be lost, or I would just wipe it out and start over.

Any ideas? Bright ideas are preferred, but I will take a look at anything at this point.

Please post the result here and wrap up the text with "CODE" tags.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Carcharoth on 2011-07-18
thanks, I will have to get to it tomorrow.
it will be a learning thing.

---

### Post by amjjawad on 2011-07-19
> **Carcharoth said:**
> thanks, I will have to get to it tomorrow.
it will be a learning thing.

Waiting for your reply :)
Every thing well explained in that link so don't worry about any thing ;)

---

