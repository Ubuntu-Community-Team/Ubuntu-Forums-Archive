---
title: "Recover GRUB after Windows Install"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by 1packer on 2010-01-18
So I'm not really a beginner, but this is kind of a beginner issue. I just reinstalled Windows Vista so I could dual boot it, but I cannot recover GRUB because the only live cd I have is Ubuntu 8.10, which refuses to mount my file system because it is ext4. Does anyone know how to recover grub in this situation?

---

### Post by synapsys on 2010-01-18
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by 1packer on 2010-01-18
How do I use this? I downloaded the USB version but their help file is off line and I am not familiar with how to put .tar.gz onto a USB drive.

---

### Post by synapsys on 2010-01-18
Extract it to the root of the drive. If you can't figure it out, burn a cd.

---

### Post by 1packer on 2010-01-18
I would try to make a cd but I am currently running in a live cd and only have one drive. Any other suggestions?

---

### Post by synapsys on 2010-01-18
Mount usb stick (places, usb stick)

Extract tar.gz to usb stick

```
tar xvfz filename.tar.gz /path/to/usbstick/
```

Then try to boot from the usb stick and see what happens...

---

### Post by 1packer on 2010-01-18
It quits with errors when trying to install it, then just says no kernel available when trying to boot on it.

---

### Post by tad1073 on 2010-01-18
> **1packer said:**
> I would try to make a cd but I am currently running in a live cd and only have one drive. Any other suggestions?

Work in vista...

download 9.10, burn it, then recover grub.

---

