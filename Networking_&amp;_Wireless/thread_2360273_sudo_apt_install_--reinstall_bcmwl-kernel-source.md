---
title: "sudo apt install --reinstall bcmwl-kernel-source"
date: 2017-05-02
forum: Networking &amp; Wireless
---

### Post by camilorc on 2017-05-02
hi, please help 

```
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/bcmwl-kernel-source.0.crash'
Error! Bad return status for module build on kernel: 4.8.0-49-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more information.
modprobe: ERROR: could not insert 'wl': Required key not available
update-initramfs: deferring update (trigger activated)
Procesando disparadores para initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.8.0-49-generic

```

[http://paste.ubuntu.com/24502763/](http://paste.ubuntu.com/24502763/)

Thanks!!!

---

### Post by wildmanne39 on 2017-05-02
This > Required key not availablemeans you need to turn secure boot off then it can load but I am not sure about the other errors. If it does not work after you turn secure boot off then please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by wildmanne39 on 2017-05-02
*Thread moved to **Networking & Wireless**.*

---

