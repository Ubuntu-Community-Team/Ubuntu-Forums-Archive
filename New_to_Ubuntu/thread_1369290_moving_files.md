---
title: "moving files"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by djen9999 on 2009-12-31
I lost my GRUB and keep booting into the MEM test.  I want to reinstall 9.10 but I need to move my home file to my external hard drive.  I don't have permission to move files with my live CD.

I know there is a command to gain permission but my wife and I just moved and I can't find my notes.  Can someone help?

Thanks.

---

### Post by Gone fishing on 2009-12-31
Alt F2 then gksu nautilus should bring up nautilus with all the privileges you need

---

### Post by SuperSonic4 on 2009-12-31
or ```
sudo mv -vu *src* *dest*
```

---

### Post by melrokz on 2009-12-31
Why dont u just reinstall grub :-)

---

### Post by djen9999 on 2010-01-01
Thanks guys,

SuperSonic4 had the command I was looking for but I ended up using Gone fishing's method.  I'm not afraid of the terminal but being able to use Nautilus directly was a plus for me.

---

