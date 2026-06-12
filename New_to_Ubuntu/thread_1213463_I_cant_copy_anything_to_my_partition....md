---
title: "I cant copy anything to my partition..."
date: 2009-07-14
forum: New to Ubuntu
---

### Post by Darkoblivion2 on 2009-07-14
hi all...

ok so, i have a western digital 1TB hdd.

when i installed jaunty i allocated 500gb for my root partition(ext3), 25bg for swap, and 475gb for free space(ext3)...

but now i cant copy anything to that free space... and when i right click in that free space partition, i cant create new folder...

what should i do in gparted to fix this?

ps... ubuntu is the ONLY os i have installed, no dual booting here...

---

### Post by Darkoblivion2 on 2009-07-14
shameless bump...

any help please?

---

### Post by oldos2er on 2009-07-14
Can you run
```
sudo fdisk -l
``` in a terminal, and post the output here?

---

### Post by HereInOz on 2009-07-14
Have you actually mounted that partition as something, somewhere?  Did you make it your home partition or did you just format it as ext3 and not put in a mount point when you installed the system?

---

### Post by Yvan300 on 2009-07-14
Well something similar happened to me when i installed Mint, something about my partition belonging to root, thus i did not have the premission to write to the filesystem. You can try using a different format or a differernt version of ubuntu. Good luck !

---

### Post by juancarlospaco on 2009-07-14
**Yes.**
Thats perfect, you can't copy anything, root can copy anything .

---

### Post by Darkoblivion2 on 2009-07-14
i found a fix, tyvm for the replies, but all is well now!

---

### Post by Yvan300 on 2009-07-15
Well if you found a fix, post it here so that others may benefit.

---

### Post by Darkoblivion2 on 2009-07-15
i posted in the gen help too...

heres how i solved it:

```
gksudo nautilus
``` Navigate to the partition mountpoint, rightclick, properties, permissions.

---

