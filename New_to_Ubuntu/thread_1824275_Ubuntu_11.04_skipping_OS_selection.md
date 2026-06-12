---
title: "Ubuntu 11.04 skipping OS selection"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by greenelf on 2011-08-13
I had installed Ubuntu 11.04 via Wubi, but I uninstalled it. Then, I installed it with the Live CD. I selected "Install along Windows." When I reboot, it automatically goes to ubuntu. How do I boot to windows?

---

### Post by bcbc on 2011-08-13
First thing to try is drop to a terminal (Ctrl+Alt+T) and run:
```
sudo update-grub
```

If that doesn't detect Windows, please post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/")

---

### Post by Basher101 on 2011-08-13
Do you see the grub menu on startup? it gives you these (default) options on bootup:
1. Ubuntu
2. Ubuntu (recovery mode)
3. Memtest86+
4. Windows

where the ubuntu entries are you can see the kernel version (2.38-10 or sth like that). If you do not see the grub menu, reply

---

### Post by greenelf on 2011-08-13
> **Basher101 said:**
> Do you see the grub menu on startup? it gives you these (default) options on bootup:
1. Ubuntu
2. Ubuntu (recovery mode)
3. Memtest86+
4. Windows

where the ubuntu entries are you can see the kernel version (2.38-10 or sth like that). If you do not see the grub menu, reply

No, I see the startup screen (logo of Compaq), then my monitor goes blank for 5 seconds, giving me an "Out of Range" error, and then I see the ubuntu blinking line at the top right.

---

### Post by greenelf on 2011-08-13
> **bcbc said:**
> First thing to try is drop to a terminal (Ctrl+Alt+T) and run:
```
sudo update-grub
```

If that doesn't detect Windows, please post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/")

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows Recovery Environment (loader) on /dev/sda3

---

### Post by bcbc on 2011-08-13
So the grub menu does contain an entry for Windows, so it's possible that the grub menu is just not displaying due to some graphics issue:

Edit the grub defaults:
```
sudo nano /etc/default/grub
```

Change 
```
GRUB-GFXMODE=auto
```
to
```
GRUB-GFXMODE=text
``` (no # at the beginning of the line). Press Ctrl+O to save, and Ctrl+X to exit.
Then update grub:
```
sudo update-grub
```

---

### Post by bcbc on 2011-08-13
By the way, grub does a lousy job of differentiating between windows recovery and the actual windows install. Check which partition has the boot flag - that's the one you want to select from the grub menu:

e.g. if "sudo fdisk -l" (lower case -L) shows the boot flag on /dev/sda3 then pick that one even though it says "recovery".

---

### Post by greenelf on 2011-08-13
> **bcbc said:**
> So the grub menu does contain an entry for Windows, so it's possible that the grub menu is just not displaying due to some graphics issue:

Edit the grub defaults:
```
sudo nano /etc/default/grub
```

Change 
```
GRUB-GFXMODE=auto
```
to
```
GRUB-GFXMODE=text
``` (no # at the beginning of the line). Press Ctrl+O to save, and Ctrl+X to exit.
Then update grub:
```
sudo update-grub
```

It worked, thanks!

---

### Post by bcbc on 2011-08-13
Great!

There may be a more refined solution - text is a bit of a sledgehammer. So if it bothers you, experiment with some other options. Here's some documentation: [https://help.ubuntu.com/community/Grub2#Configuring GRUB 2](https://help.ubuntu.com/community/Grub2#Configuring GRUB 2)

Another option would be to search on your hardware specs and see if there are any posts with fixes.

---

