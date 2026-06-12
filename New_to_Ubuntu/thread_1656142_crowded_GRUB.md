---
title: "crowded GRUB"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by oxygenfarm on 2010-12-30
After using Update Manager my GRUB screen still shows older kernels (2.6.35-22 etc). How can I safely remove these references to simplify the display?
Many thanks.

---

### Post by Verbeck on 2010-12-30
you can remove them from synaptic
just search for the version and remove the linux-headers-2.6.xx-xx and linux-image-2.6.xx-xx


edit: as a precaution, do the following
to find the kernel you're currently using:
```

uname -r

```to find all the kernel versions installed:
```

ls /boot | grep vmlinuz | cut -d'-' -f2,3

```

---

### Post by kgarbutt on 2010-12-30
Download the deb file for Ubuntu Tweak and go to package cleaner. Ubuntu Tweak will do it for you.

---

