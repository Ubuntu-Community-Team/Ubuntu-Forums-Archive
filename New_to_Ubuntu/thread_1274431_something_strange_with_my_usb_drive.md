---
title: "something strange with my usb drive"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by heyyy on 2009-09-24
on my usb i had some files which i transfered them to my pc and them permately delete them and then i ejected it having the impression that it was empty...
but when i reconnected it some of the files were still there..
i tried to delete them but i couldnt ,
so i tried to change the permissions(through right click) but i couldnt either.
can anyone tell me why is this happening and how to get rid of them?
maybe a sudo-command would do the trick...?
but again why?

---

### Post by Bucky Ball on 2009-09-24
With the drive plugged in and switched on paste:

```
gksudo nautilus
```

... into a terminal and then delete the files. Did it work?

---

### Post by heyyy on 2009-09-24
> **Bucky Ball said:**
> With the drive plugged in and switched on paste:

```
gksudo nautilus
```

... into a terminal and then delete the files. Did it work?

no it didnt worked

---

### Post by Keith Hedger on 2009-09-24
If you have removed everything you need from the stick why not just re-format it?

---

### Post by HarrisonNapper on 2009-09-24
Are these files or folders you've seen before? You might try posting the names of the files/folders if it's not personal info, as those files may have shipped with the usb.

---

### Post by heyyy on 2009-09-24
> **HarrisonNapper said:**
> Are these files or folders you've seen before? You might try posting the names of the files/folders if it's not personal info, as those files may have shipped with the usb.

i created(or at least i tried to:it told me that the operation was successful..) a new partition on the usb with partition editor which i hoped that these files would be deleted but no: they are still there..
these files are some random files i downloaded with torrents
2 pdf,1 mov and 1 avi file.

---

### Post by heyyy on 2009-09-24
> **Keith Hedger said:**
> If you have removed everything you need from the stick why not just re-format it?
how?

---

### Post by Bucky Ball on 2009-09-24
Partition Editor with the USB dongle plugged in and wipe it.

---

### Post by Sarmacid on 2009-09-24
Maybe the USB is being mounted as read only. Type mount and post the line with your usb.

---

### Post by Bucky Ball on 2009-09-24
Better still try:

```
sudo mount -a
```

---

