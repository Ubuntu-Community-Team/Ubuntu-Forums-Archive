---
title: "old kernel removal"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by eddski on 2009-09-05
I have several kernels in /boot and wanted to know the correct way to remove them and fre up some space on /boot. Should I just remove them from /boot along with their entries in menu.lst or are there additional things I need to do to cleanup? Of course I will wait a while to make sure everything works before deleting anything.

---

### Post by starcraft.man on 2009-09-05
Nope, ya just delete em. Nothing special to do.

```
sudo apt-get autoremove
```

usually works. Some people had bad experiences with autoremove though, ya can just remove em manually. Open synaptic manager and search for the version (i.e. 2.6.28 ) or so, and remove everything but latest. As always ensure kernel is working fine for ya before.

Ya can just comment out entries if ya wish to play safe, kernels are only about 100mb each, most people's root is much larger.

---

### Post by Sealbhach on 2009-09-05
You can do it in Synaptic, search for "linux-image". If you mark them for complete removal it will remove the headers as well.

.

---

### Post by eddski on 2009-09-06
thanks for reply you guys(girls) are the best!

---

