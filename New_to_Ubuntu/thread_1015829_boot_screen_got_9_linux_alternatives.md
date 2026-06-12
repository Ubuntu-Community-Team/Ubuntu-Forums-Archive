---
title: "boot screen got 9 linux alternatives"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by hatten on 2008-12-19
my boot screen has got four different kernels, recovery mode for each one of them, the memtest and XP. Why on earth is there 4 different linuxes? I have only installed it once and when i boot others than the first that i mostly use i see no difference

> 
Ubuntu 8.10, kernel 2.6.27-9-generic
Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.24-22-generic
Ubuntu 8.10, kernel 2.6.24-22-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.24-21-generic
Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.24-19-generic
Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode)
memtest86
Other operating systems
Microsoft Windows XP Home Edition

---

### Post by chrisod on 2008-12-19
When you upgrade the previous kernel is kept in case something goes wrong and you want to roll back. You can control how many previous kernels are maintained in Synaptic.

---

### Post by Elfy on 2008-12-19
As kernels get updated they are added to menu list. It's useful to have at least the 2 newest - if one has a problem, the other will work.

Open synaptic and search for linux-image and mark the older ones for complete removal, once it's finished grub will be updated and the older ones will be removed from the menu list.

---

### Post by hatten on 2008-12-19
but i have only upgraded once, from 8.04 to 8.10

where and how in synaptic?

---

### Post by taurus on 2008-12-19
Those are the kernels.  You can edit /boot/grub/menu.lst and delete the old ones except the first two kernels, 2.6.27-9-generic & 2.6.24-22-generic.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
Then, you can go into synaptic and remove those old kernels.

---

### Post by Elfy on 2008-12-19
> **hatten said:**
> but i have only upgraded once, from 8.04 to 8.10

where and how in synaptic?

So you upgrade to 8.10 and it left the old kernels there, open synaptic and use search.

---

### Post by decoherence on 2008-12-19
> Ubuntu 8.10, kernel 2.6.27-9-generic
Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.24-22-generic
Ubuntu 8.10, kernel 2.6.24-22-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.24-21-generic
Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.24-19-generic
Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode)

The top two are from 8.10 which uses kernel 2.6.27. The -9 at the end signifies (i believe) that this is ubuntu's 9th bugfix release of the .27 kernel.

The rest are from 8.04, despite what it says -- you have the 19th release, the 21st and the 22nd. These are bugfix releases which happen between distribution upgrades.

---

### Post by hatten on 2008-12-19
solved :popcorn:

now i found out how to disable the boot menu and reduce the countdown too!

---

