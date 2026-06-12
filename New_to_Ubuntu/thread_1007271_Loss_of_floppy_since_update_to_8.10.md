---
title: "Loss of floppy since update to 8.10"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2008-12-10
Since updating to Ibex I seem to have lost access to my floppy drive , though it works o.k. in Windows and on an copy of Hardy . I have tried fdisk -l and it is not listed also not in fstab. Of course I cannot mount it as the system says it is not present. Do not use it very often but just curious.

---

### Post by Michael.Godawski on 2008-12-10
Try this in terminal

```
modprobe floppy
```can you please also post the output from:
```

cat /etc/modules
```

---

### Post by ex-wirecutter on 2008-12-10
Modprobe floppy shows no results

cat /etc/modules shows fuse lp

---

### Post by Michael.Godawski on 2008-12-10
Open the modules file with

```
gksudo gedit /etc/modules
```

and add this line
```

floppy
```

save and restart.

---

### Post by ex-wirecutter on 2008-12-10
Thanks for that , have had a couple of problems with 8.10 , glad I still have a copy of Hardy which I can still use .

---

