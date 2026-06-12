---
title: "Triple boot on 3 HDDs"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by Zakarum on 2010-06-15
Hi there. 

Nowdays i'm running a dual boot Seven/Ubuntu on my laptop. I had not much problems installing it on different partitions. Today i bought a new PC and I plan to put Ubuntu 10.4/Seven/XP on the same machine but on different HDDs. I've already install the XP and seven, but as my little experience says.. I always have some problem installing Ubuntu's Grub when there's already any OS installed :D

I've read many triple boot guides around but all seems to be based on a same disk with different partitions, so... Do anyone know any guide explaining the steps that I should follow to not lose anything?

Thanks in advance.

---

### Post by Chesamo on 2010-06-15
In my experience, just make sure the Ubuntu drive is the first in the boot order (or the IDE0/Master) and that it's installed onto the MBR of that drive. The Ubuntu installation should detect your other OSs before installing GRUB.

---

