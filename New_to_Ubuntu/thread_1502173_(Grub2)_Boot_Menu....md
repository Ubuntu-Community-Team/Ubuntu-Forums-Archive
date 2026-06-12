---
title: "(Grub2) Boot Menu..."
date: 2010-06-05
forum: New to Ubuntu
---

### Post by elcartero on 2010-06-05
....getting larger.
Is there any safe way to remove redundant entries from the boot menu as each kernel upgrade adds another line to the menu?
Thank you.

---

### Post by TeoBigusGeekus on 2010-06-05
Open Synaptic Package Manager and search for linux-image.
Keep the last two kernels and completely remove the other ones.
Then open terminal and
```
sudo update-grub
```
This way, you will not only clean up grub, but your filesystem as well.

---

### Post by elcartero on 2010-06-05
Many thanks for your very quick reply, TeoBigusGeekus.
Worked perfectly..much tidier now...thanks again....Steve





> **TeoBigusGeekus said:**
> Open Synaptic Package Manager and search for linux-image.
Keep the last two kernels and completely remove the other ones.
Then open terminal and
```
sudo update-grub
```
In this way, you will not only clean up grub, but your filesystem as well.

---

