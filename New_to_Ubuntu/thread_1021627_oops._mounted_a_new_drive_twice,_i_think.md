---
title: "oops. mounted a new drive twice, i think"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by ah pook on 2008-12-25
Xmas, got a new drive from my kid, installed it, ran thru the install setup found here; seems like i typed:

sudo mount /dev/sdd1 /media/

twice. so now i have disk and disk 1 in the same place. any ideas on how to get rid of disk 1? and now that my other two HD's are disk 2 and disk 3, how do i get them back to normal. Not that I'm sure what normal was, but, you know...

---

### Post by taurus on 2008-12-25
If you want to unmount /media/disk-1, open a terminal and type

Applications -> Accessories -> Terminal
```
sudo umount /media/disk-1
df -h
```
By the way, it's better to mount it to somewhere like /media/share instead of /media as your mount point.

---

### Post by ah pook on 2008-12-25
I'm not arguing, but why is it better? What's wrong with mounting things to /media?

I'm going to defer to the experts here...just curious.

---

