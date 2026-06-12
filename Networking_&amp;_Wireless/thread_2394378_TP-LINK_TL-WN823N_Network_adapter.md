---
title: "TP-LINK TL-WN823N Network adapter"
date: 2018-06-15
forum: Networking &amp; Wireless
---

### Post by xbr0ther on 2018-06-15
Hello, 
I have the same problem, my wifi-adapter don't starts automatically if I restart my station or if I chose disable/enable wifi.

lsmod:

lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
i915                 1830912  103
i2c_algo_bit           16384  1 i915
drm_kms_helper        167936  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  2
libahci                32768  1 ahci
r8169                  86016  0
mii                    16384  1 r8169
drm                   360448  6 i915,drm_kms_helper
video                  40960  1 i915


lsusb:
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 006: ID 2357:0109  
Bus 003 Device 005: ID 09da:f663 A4Tech Co., Ltd. 
Bus 003 Device 004: ID 1a2c:0c23 China Resource Semico Co., Ltd 
Bus 003 Device 002: ID 0d8c:0012 C-Media Electronics, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Please help !
Good day from Romania !

---

### Post by jeremy31 on 2018-06-15
Split from [https://ubuntuforums.org/showthread.php?t=2386203](https://ubuntuforums.org/showthread.php?t=2386203)  What Ubuntu version are you using and what kernel?  ```
uname -r
```
I can only know that you are not using kernel 4.15 
```
sudo update-usbids
```
And the 2357:0109 device should show more info in lsusb results

---

### Post by praseodym on 2018-06-16
rtl8192eu chipset, should be supported from kernel 4.10 with module rtl8xxxu

---

