---
title: "Error when trying to install, re-install, or remove"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by TRex on 2011-08-31
Everything seemed and I hadn't made any changes for weeks, but I recently started having problems with viewing Flash videos, so I tried to re-install. I get the following errors:

E: linux-image-2.6.38-11-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

I've tried re-installing grub, got this error. I tried removing the grub customiser, got the same error (but it seems to be gone). I tried installing asunder, got errors (but it seems to be installed, but not working properly).

What should I try?

---

### Post by Rubi1200 on 2011-09-02
Try running the following commands and post any error messages you receive:

```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get install -f
sudo dpkg -- configure -a
sudo apt-get update
```

Thanks.

---

### Post by TRex on 2011-09-05
I went ahead and uninstalled grub customizer, grub-fgxpayload-lists, grub-pc, and grub -- moved /boot/grub to /boot/grub_OLD -- and then reinstalled grub and its dependencies.

I couldn't get grub-customizer to work (it asks for password, starts to load, and then shuts down), but I can live with that. Installations are once again working without error.

---

