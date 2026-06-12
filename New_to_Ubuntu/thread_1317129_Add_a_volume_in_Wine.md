---
title: "Add a volume in Wine"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by muncy on 2009-11-06
I would like to clear some space by moving a load of data to a mountable volume but this data is used by a windows program that I run in Wine. I've gone to Wine Configuration and clicked on the drives tab but I can not see how to tell Wine to look at a mountable volume.

Any ideas? Thanks

---

### Post by snkiz on 2009-11-06
Were you planing to move you entire wine directory? If so you could just empty your wine folder to the removable media then mount it in you wine folder.
```

sudo mount /dev/sdx /home/username/.wine

```
of course replace the sdx with you drive and username with yours.

---

### Post by muncy on 2009-11-06
Thanks for the reply snkiz.

I wasn't planning to move the whole directory but my problem is knowing the path to the volume. I should explain that the volume is actually another partition on my hard disk. It appears under 'Places' as 88gb Media and I click on it to mount it whenever I want to use it.

---

