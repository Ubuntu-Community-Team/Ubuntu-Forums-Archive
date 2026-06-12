---
title: "grub loading, error 17"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by vooolt on 2010-05-20
Hi All
I'm "very" new to Linux environment, from 3 days i installed Ubuntu 9.04 besides my windows xp, but today at booting my computer i found the following error:
Grub loading stage 1.5
Grub loading, please wait
Error 17

i found posts about this topic, but when i write:
sudo grub
grub> find /boot/grub/stage1
from the live CD, i found:
File not found.

i can't understand the problem,what can i do?
please, in a simple way.

Thanks.

---

### Post by -humanaut- on 2010-05-20
Can you boot the LiveCD open a terminal and type: sudo fdisk -l

then post the results back here?

---

### Post by vooolt on 2010-05-21
Thanks a lot 4 reply, it's ok now.
i looged through the live CD and typed:
sudo grub
 grub > find /boot/grub/stage1

it returned: (hd0,5)
i typed:
root (hd0,5)
setup (hd0)
quit

It's ok now, the same error appears but for less than 1 second before booting, then it boots naturally.

---

