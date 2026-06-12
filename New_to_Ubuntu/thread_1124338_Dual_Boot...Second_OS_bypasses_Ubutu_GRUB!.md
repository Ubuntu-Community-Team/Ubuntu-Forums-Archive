---
title: "Dual Boot...Second OS bypasses Ubutu GRUB!"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by Flywaver on 2009-04-13
Greetings,

I have Ubuntu Jaunty (dev/sda1) and I created a second partition to install another linux distro (dev/sda2)...both are primary partitions and I can install the scecond distro but once it's installed and reboots, it removes Ubuntu from GRUB.

So far, I managed to get Ubuntu to work again (thanks to GAG) and now the second OS doesn't show!

so....I grabbed the second OS's UUID, Kernel and initrd and I copy/pasted it in menu.lst! Now, when I go to GRUB's menu, I can clearly see:

```
title		Linux Mint 6 XFCE, kernel 2.6.27-7-generic
uuid		ad989823-946c-4f0c-bd7e-7290c08b3433
kernel		/boot/vmlinuz-2.6.27-7-generic root=ad989823-946c-4f0c-bd7e-7290c08b3433 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
```

then I select this OS and it starts to load but nothing else happens...only a blank screen! :(

Any help would be appreciated!!

---

### Post by Eisenwinter on 2009-04-13
Get on Linux Mint, open up the terminal, and mount Ubuntu's partition where the directory /boot/grub is at.

Open that directory, and copy the Ubuntu section from the file menu.lst into the newly installed GRUB.

---

### Post by Flywaver on 2009-04-13
> **Eisenwinter said:**
> Get on Linux Mint, open up the terminal, and mount Ubuntu's partition where the directory /boot/grub is at.

Open that directory, and copy the Ubuntu section from the file menu.lst into the newly installed GRUB.

See, I can't boot in Linux Mint!! :(
Only in Ubuntu!

---

### Post by Eisenwinter on 2009-04-13
Okay... so mount the Linux Mint /boot (if you have one, root in case you don't) partition, open it's /boot/grub/menu.lst file, and copy the the Linux Mint section.

---

### Post by Flywaver on 2009-04-13
> **Eisenwinter said:**
> Okay... so mount the Linux Mint /boot (if you have one, root in case you don't) partition, open it's /boot/grub/menu.lst file, and copy the the Linux Mint section.

Here is my updated menu.lst (from Ubuntu):

```
title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid		186fef91-302d-4dad-bab2-bc244e937820
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=186fef91-302d-4dad-bab2-bc244e937820 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
uuid		186fef91-302d-4dad-bab2-bc244e937820
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=186fef91-302d-4dad-bab2-bc244e937820 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu jaunty (development branch), memtest86+
uuid		186fef91-302d-4dad-bab2-bc244e937820
kernel		/boot/memtest86+.bin

title		Linux Mint 6 XFCE, kernel 2.6.27-7-generic
uuid		ad989823-946c-4f0c-bd7e-7290c08b3433
kernel		/boot/vmlinuz-2.6.27-7-generic root=ad989823-946c-4f0c-bd7e-7290c08b3433 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet
```

See...the Linux Mint is there, it can be selected in GRUB but then nothing happens! :(

I grabbed it's UUID and kernel and initrd directly from Mint's menu.lst file!

---

### Post by Eisenwinter on 2009-04-13
Get rid of UUID.

Replace that with:
```
root hd(X,X)
```

For example, say you have /dev/sda and /dev/sdb.

hd(0,0) means /dev/sda1.
hd(1,3) means /dev/sdb4
hd(0,5) means /dev/sda6
hd(0,1) means /dev/sda2
and so forth.

Replace the uuid for Linux Mint with root hd(X,X)

EDIT:

My answer was a bit unclear.

root, in grub, means where the kernel is installed.

If your kernel is installed on /dev/sda1, then you use root hd(0,0) - follow the examples of numbering above to understand what numbers you need to use, according to your partitioning scheme.

---

### Post by Flywaver on 2009-04-13
ok if I put this:

```
title		Linux Mint 6 XFCE, kernel 2.6.27-7-generic
root hd(0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=ad989823-946c-4f0c-bd7e-7290c08b3433 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet
```

It gives the following error: Unrecognized Device String

I then tried this:

```
title		Linux Mint 6 XFCE, kernel 2.6.27-7-generic
kernel		/boot/vmlinuz-2.6.27-7-generic
root hd(0,1) ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet
```

This generated this error: File Not Found! :(

---

