---
title: "how I can map local folders to eachother?"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by legolas_w on 2009-05-10
Hi
thank you for reading my post
imagine I need to do something like the following mapping in the fstab file.

Map  /media/porter/OLD to /media/OLD. while the porter is sdb5 and its format is NTFS. I need to do the above to ensure any link that I have in my desktop will continue working.

I tried the below syntax but it does not works. If you know how I can do this please let me know.


/media/porter/OLD   /media/OLD

---

### Post by Bölvaður on 2009-05-10
tell me if Im misunderstanding you. But wouldn't this be your solution:

Right click the  /media/porter/OLD directory and select "Make link".
Then cut it into /media and rename it.

---

### Post by blueridgedog on 2009-05-10
You could try ln:

```
ln /media/porter/OLD /media/OLD -s
```

man ln for more infor.

---

### Post by uncannybuzzard on 2009-05-10
you can also mount folders so they exist in two places at once. add this to your fstab:

```
/path/of/source/  /other/mount/point/    none    bind    0       0
```

then run:

```
sudo mount -a
```

this is actually more useful if you need to get around chrooting.

---

