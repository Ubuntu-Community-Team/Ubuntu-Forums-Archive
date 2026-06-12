---
title: "grub still shows deleted kernels"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by darshan123 on 2010-10-24
Hi,

I am using ubuntu 10.05. Earlier i was using a older version (9.10) and instead of upgrading it i had installed 10.05 seperately (on a diff partition). The grub used to show 2 linux options. That's fine. But now, I have deleted the old partition and the grub shows an entry for old version even though the kernel isn't there ! How do i actually remove that entry ?

In my /boot there is only one kernel (2.6.32-25). Nothing else.
Even synaptic manager doesn't show anything old.

Regards,
Darshan

---

### Post by Elfy on 2010-10-24
```
sudo update-grub
```

---

