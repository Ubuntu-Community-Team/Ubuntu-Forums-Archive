---
title: "How to remove the many options in the bootup screen?"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by kinngg on 2009-03-13
Hi all, you know when you first turn on your laptop, you're in the screen which gives you the option to select which OS you want to start up. I have so many different links because i have updated my ubuntu several times and every time i update my ubuntu, a new line would appear. How can i remove the unecessary ones?

---

### Post by taurus on 2009-03-13
Go into System -> Administration -> Synaptic Package Manager -> Search and type in **linux-image**.  Then, highlight the old kernels that you want to remove and remove them.  Now, look in /boot/grub/menu.lst if the entries for those old kernel are still there.  If they are, you can edit/remove them from /boot/grub/menu.lst.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by issih on 2009-03-13
Alternatively just go into Startup manager, its under the system menu somewhere (I'm not at my pc so I can't check). In that dialog find the setting for the number of kernels to keep and set that to something smaller. I suggest not less than 2 in case a kernel upgrade drops you in the brown smelly stuff at some point.

---

### Post by BOZG on 2009-03-13
If you'd rather use a GUI instead of directly editing the boot menu, try Start-Up Manager:

```
sudo apt-get install startupmanager
```

You should find it under System -> Administration (or possibly Preferences).

---

### Post by Therion on 2009-03-13
Install **Startup Manager**:```
sudo aptitude install startupmanager
```
Go to:  System > Administration > Startup Manager > Advanced tab.

Click on: Limit the number of kernels to keep.

---

### Post by issih on 2009-03-14
Um...yeaah you may want to install the startup manager package first as the guys above said, oops :s

---

### Post by Troll_the_Great on 2009-03-14
> **taurus said:**
> Go into System -> Administration -> Synaptic Package Manager -> Search and type in **linux-image**.  Then, highlight the old kernels that you want to remove and remove them.  Now, look in /boot/grub/menu.lst if the entries for those old kernel are still there.  If they are, you can edit/remove them from /boot/grub/menu.lst.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

+1. This is the best option because you will free some space on your hard drive too (several GB if you have lots of old kernels). I suggest though to leave 2 kernels, if something goes wrong in one, you can boot into the other.
Cheers!

EDIT:you can install startup manager too, it is a useful tool.

---

