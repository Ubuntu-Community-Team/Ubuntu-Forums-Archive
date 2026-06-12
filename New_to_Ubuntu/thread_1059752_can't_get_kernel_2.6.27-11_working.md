---
title: "can't get kernel 2.6.27-11 working"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by occams_beard on 2009-02-04
The other day there was a kernel update. From 2.6.27-9-generic to 2.6.27-11-generic.

As the packages were installing, a dialog box poped up and asked something like, what do you want to do with GRUB, or words to that effect. It had a drop down box with a bunch of different options, and an OK button. I didn't pay much attention, because I was in a hurry, and I figured the default would be ok.  

Apparently it wasn't because 2.6.27-11 is not in menu.lst, and I'm still stuck on the old version of the kernel. 

Any ideas how I can get the new kernel?  And what was that dialog box, and why did it show up? Never saw it before.

---

### Post by Quintus on 2009-02-04
Try opening a terminal (applications - accesores - terminal) 
and run

sudo update-grub

Then reboot

Hope this helps

---

### Post by occams_beard on 2009-02-04
The output from sudo update-grub is:

```

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

So it looks like the kernel is indeed installed, but 2.6.27-11 still does not appear in menu.lst...

---

### Post by Quintus on 2009-02-04
You have tried rebooting right?

Join the ubuntu irc support channel and ask you're question there. I'm online.

---

### Post by occams_beard on 2009-02-04
Yes, tried rebooting...

Thanks, but I think I'll wait for an answer here where other people having the same problem can benifit.

---

### Post by taurus on 2009-02-04
Edit /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```
and copy the entry for the older kernel, 2.6.27.9, but replace the older version with the newer one, 2.6.27.11.  You might want to place that new entry ahead of the older one so it would be booted automatically, default 0, after a timeout (whatever seconds you have).

---

### Post by occams_beard on 2009-02-05
Thanks. Adding the new kernel to menu.lst did the trick.

Incidentally, the problem was caused by the VirtualBox kernel modules. After booting into the new kernel, VirtualBox told me I needed to re-compile the modules. So, I'm guessing the vbox modules freaked out the kernel install, and it wasn't added to grub.

Anyway, did a sudo /etc/init.d/vboxdrv setup and all is well now.

---

