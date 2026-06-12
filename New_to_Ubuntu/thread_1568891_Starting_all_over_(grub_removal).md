---
title: "Starting all over (grub removal)"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by Goatie on 2010-09-06
Hi everybody :)

I've installed Ubuntu 10.04 on a separate hdd than my Windows XP installation to be on the safe side... grub is controlling the dualboot-thingie.

I'm in the process of moving all my important files like photos, documents and all that stuff to an external hdd because I'm getting a new cpu in a couple of days and want to make a completely fresh XP install on my main hdd and wipe out everything on the rest of the computer.
I've read a couple of threads about grub and I'm still a bit confused.

Now, here's my question:
When I pop in my Windows XP CD and boot off it to format my main hdd and make a fresh install, does it also remove grub so my computer just boots directly into Windows in the future?

---

### Post by JBAlaska on 2010-09-06
You will need to boot the xp cd and enter Recovery Console, then use the fixmbr and fixboot options

---

### Post by Goatie on 2010-09-06
Is it necesary to use the fixmbr and fixboot after a fresh and clean install of Windows XP?

---

### Post by JBAlaska on 2010-09-07
> **Goatie said:**
> Is it necessary to use the fixmbr and fixboot after a fresh and clean install of Windows XP?

As far as I remember, the XP install should overwrite the MBR. If XP boots without grub showing after you install it you should be GTG.

---

### Post by cariboo on 2010-09-07
The XP installs to the MBR during the installation procedure, so you don't have to go into the recovery console to fix the boot.

BTW, Linux isn't like Windows in that when you change hardware you don't have to do a new install, so once you have installed Windows you can chroot into your Ubuntu install with a Live CD and install grub, and your ready to go.

---

### Post by Goatie on 2010-09-07
Thanks for clearing that up for me guys :)

---

