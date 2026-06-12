---
title: "Problems installing bcmwl-kernel-source on ubuntu 16.04 with no wired connection"
date: 2018-02-25
forum: Networking &amp; Wireless
---

### Post by mattiadale on 2018-02-25
Hi, I have a HP stream on which ubuntu gnome 16.04 is installed and all of a sudden the wifi is not working anymore. I believe this is a broadcom problem since I had it already before. I tried to run the wireless-info.txt file but it gives no output, and I cannot figure out why. 

What I've been trying to do already is to reinstall bcmwl-kernel-source(_6.30.223.248+bdcom-0ubuntu8_amd64.deb), but when I do it it gives the following errors: 

```

Loading new bcmwl-6.30.223.248+bdcom DKMS files...
Building only for 4.13.0-26-generic
Building for architecture x86_64
Building initial module for 4.13.0-26-generic
Error! Bad return status for module build on kernel: 4.13.0-26-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/make.log for more information.
modprobe: FATAL: Module wl not found in directory /lib/modules/4.13.0-26-generic
update-initramfs: deferring update (trigger activated)
Elaborazione dei trigger per initramfs-tools (0.122ubuntu8.8)...
update-initramfs: Generating /boot/initrd.img-4.13.0-26-generic

```

---

### Post by jeremy31 on 2018-02-25
Please post results for ```
dkms status
```

---

### Post by mattiadale on 2018-02-25
```


bcmwl, 6.30.223.248+bdcom: added


```

---

### Post by jeremy31 on 2018-02-25
See if using this version works better [http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu1~1.2_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu1~1.2_amd64.deb)
I can't find anything in the changelog for your version that shows it is patched for the 4.13 kernel

---

### Post by mattiadale on 2018-02-25
It works! Thank you very much

---

