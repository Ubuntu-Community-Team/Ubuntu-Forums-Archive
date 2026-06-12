---
title: "How to move a file greater than 4GB through FAT32?"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by halo45121 on 2011-02-19
I've got a 4.6GB .iso file on my Ubuntu laptop that I need to copy to my FAT32 external hard drive, and then move to another computer (Windows). I know that FAT32 has a 4GB limit, and that I need to split the file. I don't know how to do that, and I have no idea how I'll put it back together once it gets to the Windows computer. Help?

---

### Post by Hippytaff on 2011-02-19
can't you compress/zip it?

---

### Post by n-n-nebbl on 2011-02-19
> **Hippytaff said:**
> can't you compress/zip it?

For this, you just have to right click on the file and choose compress

note: not every archive type can split files ;)

---

### Post by kittkatt on 2011-02-19
Look into "file spanning" using either .zip or .rar  .  It can split up your compressed file into multiple parts and then automatically recombine them when you extract.

---

### Post by Fenderian_Mayhew on 2012-03-09
Reviving for curiosity.
~*~*~

Can't we just use cat to move the file? ie ```
cat Big.File >> /media/fat32/destination
```

---

### Post by Cheesemill on 2012-03-09
Use split and cat:

[http://www.johnrockefeller.net/linuxunix-using-split-and-cat-to-split-large-files-for-transfer/](http://www.johnrockefeller.net/linuxunix-using-split-and-cat-to-split-large-files-for-transfer/)

---

