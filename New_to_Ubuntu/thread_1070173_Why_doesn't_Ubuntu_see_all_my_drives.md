---
title: "Why doesn't Ubuntu see all my drives?"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by jkauff on 2009-02-14
I've installed 8.10 via the Wubi installer, and Ubuntu only mounts about half of my NTFS drives. I manually mounted a couple, but the others don't show up at all.

Any suggestions?

---

### Post by louieb on 2009-02-14
Do you see the missing partitions when you run```

sudo fdisk -l
``` (lowecase L at the end)??

---

### Post by DigiTan on 2009-02-15
I had a problem like this today.  Ubuntu was seeing optical drives, but not SATA drives.  At the boot menu, I pressed the "options" key and added **irqpoll** to the text line that appears.  That fixed it.

---

