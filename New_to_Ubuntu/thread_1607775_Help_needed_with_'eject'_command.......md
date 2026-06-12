---
title: "Help needed with 'eject' command......"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by elcartero on 2010-10-28
Due to problems with a new ATX desktop case I've just had fitted I need to eject my DVD-Rom and DVD-Burner using the command line.
I can eject my empty DVD-Rom using the command 'eject cdrom' but am unable to find the command to eject my DVD-Burner.
Can anyone help please so that I can use the burner until the shop refits the case.
Thank you.

---

### Post by TeoBigusGeekus on 2010-10-28
Try
```
eject /dev/dvd
```
or 
```
eject /dev/dvdrw
```

---

### Post by ibizatunes on 2010-10-28
Is your cd drive mounted?
If it make sure nothing is accessing it, or that your cd to the directory by mistake!
cd /
eject cdrom

---

### Post by cjv8888 on 2010-10-28
Try

```
eject cdrom0
```

or

```
eject cdrom1
```

---

### Post by ArgusVision on 2010-10-28
cjv8888 is on the right track. With multiple devices they'll be numbered 0 through whatever. You can use the command ```
ls /dev
```
to see what devices you have available.

---

### Post by elcartero on 2010-10-28
My very grateful thanks to all who replied so promptly to my problem which is now solved.
The command turned out to be 'eject dvd2' should anyone else have the same problem.
Thanks again to you all.

---

