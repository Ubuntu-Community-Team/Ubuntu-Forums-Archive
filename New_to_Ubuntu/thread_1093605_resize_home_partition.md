---
title: "resize home partition"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-03-11
is it possible to make it larger?  i realize now i created it too small

---

### Post by bodhi.zazen on 2009-03-11
Yes, use gparted from a live CD.

---

### Post by mamamia88 on 2009-03-11
cool thanks

---

### Post by mamamia88 on 2009-03-11
ok i schrunk my root but it won't let me make home bigger any reason or advice?

---

### Post by bodhi.zazen on 2009-03-11
It would help if you posted a screen shot of gparted ;)

My first guess is you need to :

shrink / -> apply changes

Then make /home bigger -> apply changes

---

### Post by mamamia88 on 2009-03-11
thats what i tried to do but ill post a screenshot

---

### Post by bodhi.zazen on 2009-03-11
To be honest ....

The easiest thing would be to delete the swap partition, then you will be able to resize /home , then make a new swap partition.

Basically you need the unallocated space to be adjacent to your /home and right now swap is in the way.

The alternate is to move the /home or swap

If you delete and re-create swap you will need to update /etc/fstab

---

### Post by mamamia88 on 2009-03-11
ok thanks so i just move or disable swap and i should be fine?

---

### Post by bodhi.zazen on 2009-03-11
yes :)

---

### Post by mamamia88 on 2009-03-11
ok i deleted swap and everything worked fine but how do i edit fstab?

---

### Post by bodhi.zazen on 2009-03-11
You can do it from the live cd, but probably easier to just reboot.

Then, list your partitions with 

```
sudo blkid
```

and add your swap back

```
gksu gedit /etc/fstab
```

Change the old UUID to the new.

---

