---
title: "No network devices are available - Ubuntu 16.04 LTS"
date: 2018-02-27
forum: Networking &amp; Wireless
---

### Post by mikerichards123 on 2018-02-27
I've tried to install Ubuntu 16.04 LTS on another machine and unfortunately I'm having further wireless woes. When selecting the NetworkManager icon all it shows is "No network devices are available". I thought this might be Broadcom related so I followed the pinned solution in the forum. This was the output when i ran

```
sudo dpkg -i /media//pool/restricted/b/bcmwl/bcmwl-kernel-source_*.deb
```

```

Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 211152 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu1~1.1_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu1~1.1) ...
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu1~1.1) ...
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 4.13.0-32-generic
Building for architecture x86_64
Building initial module for 4.13.0-32-generic
Error! Bad return status for module build on kernel: 4.13.0-32-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more information.
modprobe: FATAL: Module wl not found in directory /lib/modules/4.13.0-32-generic
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.13.0-32-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915
W: Possible missing firmware /lib/firmware/i915/kbl_huc_ver02_00_1810.bin for module i915
W: Possible missing firmware /lib/firmware/i915/bxt_huc_ver01_07_1398.bin for module i915
W: Possible missing firmware /lib/firmware/i915/skl_huc_ver01_07_1398.bin for module i915
```


Also, if it helps, when running 
```
lspci -knn| grep Net -A2

```

The output is:
```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: Dell BCM4352 802.11ac Wireless Network Adapter [1028:0019]
    Kernel modules: bcma

```

In trying to fix the issue it appears that I've also affected my audio driver which seems to randomly drop off and requires a restart to work again. I understand if that is a question for another thread!

Thanks in advance

---

### Post by chili555 on 2018-02-27
> Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more information.Did you? Did it say that you first have to install dkms which can also be found on the DVD or USB?

---

### Post by mikerichards123 on 2018-02-27
Thanks for your response chili555 - It doesn't say anything about installing dkms as far as I understand. This is what was in the make.log:

```
DKMS make.log for bcmwl-6.30.223.271+bdcom for kernel 4.13.0-32-generic (x86_64)
Tue 27 Feb 00:35:09 GMT 2018
make: Entering directory '/usr/src/linux-headers-4.13.0-32-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  AR      /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.o
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c: In function &#8216;wl_monitor&#8217;:
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c:2922:10: error: &#8216;struct net_device&#8217; has no member named &#8216;last_rx&#8217;
  skb->dev->last_rx = jiffies;
          ^
scripts/Makefile.build:308: recipe for target '/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.o' failed
make[1]: *** [/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.o] Error 1
Makefile:1550: recipe for target '_module_/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build' failed
make: *** [_module_/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build] Error 2
make: Leaving directory '/usr/src/linux-headers-4.13.0-32-generic'
```

---

### Post by praseodym on 2018-02-27
[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-7_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-7_all.deb)

Try this one

---

### Post by mikerichards123 on 2018-02-27
This seems to have worked! Thank you!! Will change to solved

---

