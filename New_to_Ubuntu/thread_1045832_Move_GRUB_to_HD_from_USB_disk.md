---
title: "Move GRUB to HD from USB disk"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by puelly on 2009-01-20
Hope someone can help with this prob.  I did a server install from a USB stick but the bootloader remained on the USB stick and now the server will only boot if the USB disk is in.  How can I move the bootloader to the HD.

Thanks.

---

### Post by Tim Sharitt on 2009-01-21
Try
```
grub-install --root-directory=/boot (hd0)

```
assuming the Linux kernel image is in /boot and Linux is installed to the first hard drive.

---

### Post by puelly on 2009-01-21
Thank you.

---

