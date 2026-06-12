---
title: "How to disable routine check of drives?"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by Julita on 2009-05-31
There is no necessity for me to do it, and is there a way to  disable it? I would appreciate if someone could help me...

---

### Post by racorbin2007 on 2009-05-31
from a command line:
sudo tune2fs -c 0 /dev/sda1
will disable the drive check for /dev/sda1; replace sda1 with each drive you have.

---

### Post by philinux on 2009-05-31
I would not disable this function. But instead say set it at 60 or so boots.

---

### Post by steeleyuk on 2009-05-31
I agree with philinux. The check is there for a reason, not to annoy you. If you disable it then you put your files and data at risk.

---

### Post by Julita on 2009-05-31
Thank you very much! I know that it might actually be useful; I don't care about the data loss on my computer, that's all ;)

---

### Post by CONCORAN on 2009-08-22
Is it possible to make it check disks after boot has completed (e.g, after user sees login prompt)?

---

### Post by ks07 on 2009-08-22
> **CONCORAN said:**
> Is it possible to make it check disks after boot has completed (e.g, after user sees login prompt)?
I don't think it is, as the disk checker needs access to the entire filesystem, so it has to run before everything is mounted.

---

### Post by theozzlives on 2009-08-22
In Jaunty, the time for the check is minimal and beats trying to remember to run scandisk in Windows.

---

