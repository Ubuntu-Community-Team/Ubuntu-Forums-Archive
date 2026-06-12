---
title: "getting DentryOpRevalidate when mounting / unmounting windows file shares"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by evanvliet on 2008-06-17
I'm getting the following four lines in /var/log/messages whenever I mount or umount a windows file share as a cifs file system. I've tried tweaking /etc/fstab, but always get lines like this:

Jun 17 16:01:25 sekai kernel: [17415.091301] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 17 16:01:25 sekai kernel: [17415.091405] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 17 16:01:25 sekai kernel: [17415.098640] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 17 16:01:25 sekai kernel: [17415.099328] VMBlock warning: DentryOpRevalidate: invalid args from kernel

This is Ubuntu 8.04 Hardy Heron freshly updated, running as VMWare image.

---

