---
title: "Kernel upgrade problem?"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by Paul T. on 2009-07-01
After upgrading kernel from 2.6.28-13 to 2.6.30-candela, pc re-booted fine, however after re-installing nVidia graphics driver, x-server hangs on re-boot. I've tried both 96 & 173 driver with same result each time, using recovery mode and "auto fix x-server" I was able to get desktop back on.

Can I remove this new kernel, or at least change boot menu so it defaults back to previous version?

---

### Post by Paul T. on 2009-07-01
I've figured out how to edit grub menu so it now defaults to previous version, so can I remove new kernel or do I just leave it?

---

### Post by Bucky Ball on 2009-07-01
You can comment it out of the /boot/grub/menu.lst file so it doesn't show at boot or you can uninstall. I would leave it and just comment it out and try it again later. It is 9.04 so things are still getting fixed.

After

```
sudo nano /boot/grub/menu.lst
```

you can make the changes.

```
# title           Ubuntu 8.04.1, kernel 2.6.24-16-generic
# root            (hd0,5)
# kernel          /boot/vmlinuz-2.6.24-16-generic 
# root=UUID=36bd7710-#ca84-48c9-90$
# initrd          /boot/initrd.img-2.6.24-16-generic
# quiet
```... instead of:

```
title           Ubuntu 8.04.1, kernel 2.6.24-16-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=36bd7710-ca84-48c9-90$
initrd          /boot/initrd.img-2.6.24-16-generic
quiet
```The details of your kernel will be different of course.

---

