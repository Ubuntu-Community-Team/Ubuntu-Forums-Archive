---
title: "iso game"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by mushroom08 on 2011-03-25
hi im trying to make an iso of a game i have for wine i found a walk through that tells me to use DD or data dump i have looked in synaptic and can not find it what is it and how do i install and use it?

---

### Post by PCNetSpec on 2011-03-25
It's already installed, See:
```
man dd
```
for syntax.

dd actually stands for "Data Description".

[http://en.wikipedia.org/wiki/Dd_(Unix](http://en.wikipedia.org/wiki/Dd_(Unix))

But is often referred to as disk dump, or data dump etc.

be VERY careful with the **of=** (output file) part as it is also often referred to as "data destroyer", or "delete data" ;)

---

### Post by mushroom08 on 2011-03-25
is there a better way to make a game disk ISO?

---

### Post by The_Eggert on 2011-03-25
> **mushroom08 said:**
> is there a better way to make a game disk ISO?

If it is a CD, I would use the dd command:
```

Turn a CD/DVD into an .iso
sudo umount /dev/cdrom
dd if=/dev/cdrom of=file.iso bs=1024

```

If it is a folder use the mkisofs:
```

Turn a folder into an .iso
mkisofs -r -o file.iso /location_of_folder/

```

---

### Post by PCNetSpec on 2011-03-25
Or if you want a GUI, you could try installing **isomaster**, it's in the "Universe" repo.

---

### Post by gdhamell on 2011-03-25
Thanks Eggert. I was looking for this solution as well. Love that so much stuff is built right into Ubuntu.

---

