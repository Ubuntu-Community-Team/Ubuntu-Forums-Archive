---
title: "Modifying what happens at startup."
date: 2009-03-06
forum: New to Ubuntu
---

### Post by waxyfresh on 2009-03-06
Id like to remove fschk? or whatever its called that runs the scan disk every 30-40 restarts. Also id like to edit grub to automaticly select the kernal i want instead of the one thats at the top of the list.

---

### Post by kanikilu on 2009-03-06
> **waxyfresh said:**
> Id like to remove fschk? or whatever its called that runs the scan disk every 30-40 restarts.

You can use tune2fs to change that number.

```
man tune2fs
```

> Also id like to edit grub to automaticly select the kernal i want instead of the one thats at the top of the list.

```
sudo nano /boot/grub/menu.lst
```

Change the line that says **default 0**. The number will correspond to how they are listed at the bottom of that file. Just remember that it starts at 0, so if you want the 3rd kernel to be the default, change it to **default 2**.

---

### Post by lindsay7 on 2009-03-06
Down load the "Startup Manager" using Synapic. You can choose what the start default is.

---

### Post by Paqman on 2009-03-06
> **waxyfresh said:**
> Also id like to edit grub to automaticly select the kernal i want instead of the one thats at the top of the list.

If you want a GUI way to do this, the package startupmanager can do this and a whole lot more. Very handy tool.

---

