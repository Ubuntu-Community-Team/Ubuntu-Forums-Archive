---
title: "mounting 2nd hard drive on boot"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by jonpon on 2009-08-18
Hi there,
Can any help me,
My laptop has a built-in 2nd hard drive that I use to store photos etc. To access this I use the drop menu, It works just fine, but is it not possible to mount this when I start up the computer automatically?

---

### Post by JohnFH on 2009-08-18
I know how to do it by editing a file (/etc/fstab), but maybe someone knows a way to do it by using the GUI ... anyone?

---

### Post by jonpon on 2009-08-18
> **JohnFH said:**
> I know how to do it by editing a file (/etc/fstab), but maybe someone knows a way to do it by using the GUI ... anyone?

Editing the file is fine!
 I tried changing default to auto,rw,user

```
/media/sdb1   ext3   auto,rw,user   0   2
```

but it doesn't seem to be right

---

### Post by JohnFH on 2009-08-18
Looks like you are missing the device to mount.  Should be something like: 

```

/dev/sdb1  /media/sdb1   ext3   defaults,user   0   2

```

---

