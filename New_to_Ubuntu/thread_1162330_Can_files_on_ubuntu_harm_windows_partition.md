---
title: "Can files on ubuntu harm windows partition?"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by Rigorous on 2009-05-17
Say I get a virus on ubuntu (I know it won't do anything on ubuntu), can it get to my windows partition?

Thanks!

---

### Post by The Cog on 2009-05-17
Theoretically, yes. Especially if the windows partition is mounted. But unlikely. A Linux virus is unlikely to go looking for windows files. And viruses aren't common on Linux at the moment.

---

### Post by LowSky on 2009-05-17
windows cannot natively read the file system of ubuntu.
no in the most part NO

unless the file is put into a shared directory and opened. then that may occur

---

### Post by Rigorous on 2009-05-17
Thank you for the replies! What does it mean to mount a partition if you don't mind?

---

### Post by Michael.Godawski on 2009-05-17
Check out the Community Documentation:


[LIST]
[*][https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
[/LIST]
A wonderful place. ;)

---

### Post by Rigorous on 2009-05-17
Thanks Michael.

EDIT: I just realized that you guys are thinking I ment a linux virus, I was asking if you get a WINDOWS virus, same answer I would get, I guess?

---

### Post by lavinog on 2009-05-17
I think by default a windows partition will require super user privleges to mount. In this case you have to allow the malacious program to access the windows drive.

---

### Post by OutOfReach on 2009-05-17
> **Rigorous said:**
> Thanks Michael.

EDIT: I just realized that you guys are thinking I ment a linux virus, I was asking if you get a WINDOWS virus, same answer I would get, I guess?

Well if it was a Windows virus, it probably won't even execute at all because Linux can't run .exe files (unless you have WINE), second I seriously doubt that a virus would go looking for other partitions. so theoretically, yes it is possible but not likely

my 2 cents

---

