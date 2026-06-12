---
title: "Wireless drivers bcmwl-kernel-source breaks on kernel 5.4"
date: 2019-12-15
forum: Networking &amp; Wireless
---

### Post by jinyang-liu-jl on 2019-12-15
Wireless drivers for my PCI WiFi card, does not work on the newest kernel.
```

Unpacking bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu5~18.04.1) over (6.30.223.271+bdcom-0ubuntu5~18.04.1) ...
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu5~18.04.1) ...
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
Building for 5.4.3-050403-generic
Building for architecture x86_64
Building initial module for 5.4.3-050403-generic
ERROR (dkms apport): kernel package linux-headers-5.4.3-050403-generic is not supported
Error! Bad return status for module build on kernel: 5.4.3-050403-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more information.
modprobe: FATAL: Module wl not found in directory /lib/modules/5.4.3-050403-generic
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.130ubuntu3.9) ...
update-initramfs: Generating /boot/initrd.img-5.4.3-050403-generic
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8125a-3.fw for module r8169

```

Do i have to wait for drivers to be released for the new kernel?

---

### Post by praseodym on 2019-12-15
Try "the other one":
```

sudo apt-get install broadcom-sta-dkms
```

---

### Post by jinyang-liu-jl on 2019-12-15
I already have it installed...

---

### Post by jeremy31 on 2019-12-15
Why do you need that kernel?

---

### Post by jinyang-liu-jl on 2019-12-17
amdgpu drivers have been updated, they longer work with an older kernel. Or atleast, I do not know which kernels they are compatible with other than 5.4

---

