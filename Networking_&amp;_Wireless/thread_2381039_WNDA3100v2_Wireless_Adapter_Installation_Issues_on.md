---
title: "WNDA3100v2 Wireless Adapter Installation Issues on Ubuntu 16.04.3"
date: 2017-12-25
forum: Networking &amp; Wireless
---

### Post by serkroth on 2017-12-25
Hello! 

I am having plenty of issues getting my WNDA3100v2 Wireless Adapter to function in Ubuntu 16.04.3. I have tried several tutorials I've found through Google (which I failed to copy the links for future reference), but to no avail. 

The furthest I get is being able to see that a driver (I believe it to be the correct one) is installed and active, but there is still no wireless. 

I ran through both sticky's before posting but I had no success with chili555's post (lspci -nn -d 14e4: returns nothing).



I have uploaded my wireless-info.txt file per bapoumba's thread. That file is located here: [https://paste.ubuntu.com/26254536/](https://paste.ubuntu.com/26254536/)

Please let me know if you need anymore information. I will await further instructions, if any :)

---

### Post by praseodym on 2017-12-26
[https://media-cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz](https://media-cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz)

Try this driver. You may want to change the router mode to b/g

---

### Post by serkroth on 2017-12-28
Sorry for the slow reply. An outage occurred right around the time I tried this. Maybe it was a sign? :D

I installed the drivers you posted and switched my wireless 2.4 to b/g mixed. Rebooted. No luck yet.

Looking over my wireless-info.txt file, I noticed ndiswrapper was listed twice. I deleted the second entry just in case and then rebooted.

I feel like it see's the hardware, but for whatever reason, that hardware is not enabled in some way...or am I headed in the opposite direction here?

Here is a little more info I gathered that I hope helps:

> 
lshw -C Network

```


  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 06
       serial: 44:8a:5b:5d:7c:cf
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.0.10 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:36 ioport:e000(size=256) memory:d2804000-d2804fff memory:d2800000-d2803fff
```

> dmesg | grep ndis
```
[    9.151818] ndiswrapper: loading out-of-tree module taints kernel.
[    9.151987] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[    9.151995] ndiswrapper: module license taints kernel.
[    9.152830] ndiswrapper version 1.60 loaded (smp=yes, preempt=no)
[   16.458113] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[   16.458514] Modules linked in: ndiswrapper(OE+) parport_pc ppdev lp parport autofs4 amdgpu hid_generic usbhid hid amdkfd amd_iommu_v2 nouveau radeon mxm_wmi i2c_algo_bit ttm drm_kms_helper ahci syscopyarea sysfillrect libahci sysimgblt fb_sys_fops drm r8169 mii wmi fjes video
[   16.458577]  wrap_submit_irp+0x4db/0xb00 [ndiswrapper]
[   16.458592]  pdoDispatchDeviceControl+0x2d/0x70 [ndiswrapper]
[   16.458603]  win2lin_pdoDispatchDeviceControl_2+0x18/0x20 [ndiswrapper]
[   16.458613]  ? win2lin_IoInvalidDeviceRequest_2+0x20/0x20 [ndiswrapper]
[   16.458623]  lin2win2+0xd/0x20 [ndiswrapper]
[   16.458638]  IofCallDriver+0x6b/0xc0 [ndiswrapper]
[   16.458648]  win2lin_IofCallDriver_2+0x18/0x20 [ndiswrapper]
[   16.458661]  ? ExAllocatePoolWithTag+0x37/0x50 [ndiswrapper]
[   16.458672]  ? ExAllocatePoolWithTag+0x37/0x50 [ndiswrapper]
[   16.458684]  ? ExAllocatePoolWithTag+0x37/0x50 [ndiswrapper]
[   16.458694]  ? NdisAllocateMemoryWithTag+0x16/0x30 [ndiswrapper]
[   16.458707]  ? win2lin_NdisAllocateMemoryWithTag_3+0x1b/0x30 [ndiswrapper]
[   16.458721]  ? win2lin_NdisAllocateMemoryWithTag_3+0x1b/0x30 [ndiswrapper]
[   16.458733]  ? ExAllocatePoolWithTag+0x37/0x50 [ndiswrapper]
[   16.458744]  ? ExAllocatePoolWithTag+0x37/0x50 [ndiswrapper]
[   16.458758]  ? win2lin_NdisAllocateMemoryWithTag_3+0x1b/0x30 [ndiswrapper]
[   16.458771]  ? pdoDispatchPnp+0x4a/0x490 [ndiswrapper]
[   16.458781]  ? lin2win6+0x22/0x28 [ndiswrapper]
[   16.458796]  ? mp_init+0x7a/0x260 [ndiswrapper]
[   16.458809]  ? NdisDispatchPnp+0xca/0xc70 [ndiswrapper]
[   16.458827]  ? IoAllocateIrp+0x4a/0x90 [ndiswrapper]
[   16.458837]  ? win2lin_NdisDispatchPnp_2+0x18/0x20 [ndiswrapper]
[   16.458847]  ? win2lin_NdisDispatchDeviceControl_2+0x20/0x20 [ndiswrapper]
[   16.458856]  ? lin2win2+0xd/0x20 [ndiswrapper]
[   16.458871]  ? IofCallDriver+0x6b/0xc0 [ndiswrapper]
[   16.458884]  ? IoSendIrpTopDev+0xdb/0x130 [ndiswrapper]
[   16.458897]  ? wrap_pnp_start_device+0x22e/0x2f0 [ndiswrapper]
[   16.458910]  ? wrap_pnp_start_usb_device+0xdb/0x110 [ndiswrapper]
[   16.458938]  ? loader_init+0xbc/0x140 [ndiswrapper]
[   16.458947]  ? wrapper_init+0xa1/0x1000 [ndiswrapper]
[   16.458998] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[   16.459000] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[   16.459002] ndiswrapper (mp_halt:254): device ffff9009b7cc0900 is not initialized - not halting
[   16.459002] ndiswrapper: device eth%d removed
[   16.459046] ndiswrapper: probe of 1-2:1.0 failed with error -22
[   16.459073] usbcore: registered new interface driver ndiswrapper


```

> ndiswrapper -l
```
bcmn43xx64 : driver installed
    device (0846:9011) present
```

---

### Post by praseodym on 2017-12-28
```
[   16.459000] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
```

Please shutdown for 15 minutes to unload any firmware. Please also show then
```

dpkg -l ndis* | grep ii
locate ndiswrapper.ko | grep lib
modinfo ndiswrapper
cat /etc/ndiswrapper.conf
dkms status
```

---

### Post by serkroth on 2017-12-29
Shut down my computer from Windows and let sit 15+ minutes. I then booted straight into Ubuntu, but still no wireless.

Here are the results of the commands you posted:

> dpkg -l ndis* | grep ii
```
ii  ndisgtk               0.8.5-1ubuntu1       amd64        graphical  frontend for ndiswrapper (installation of Windows WiFi drivers)
ii  ndiswrapper           1.60-3~ubuntu16.04.1 amd64        Userspace utilities for the ndiswrapper Linux kernel module
ii  ndiswrapper-dkms      1.60-3~ubuntu16.04.1 all          Source for the ndiswrapper Linux kernel module (DKMS)
ii  ndiswrapper-source    1.60-3~ubuntu16.04.1 all          Source for the ndiswrapper Linux kernel module
ii  ndiswrapper-utils-1.9 1.60-3~ubuntu16.04.1 all          Transitional dummy package upgrading to ndiswrapper
```

> locate ndiswrapper.ko | grep lib
```
/lib/modules/4.10.0-42-generic/updates/dkms/ndiswrapper.ko
/var/lib/dkms/ndiswrapper/1.60/4.10.0-42-generic/x86_64/module/ndiswrapper.ko
```

> modinfo ndiswrapper
```
filename:       /lib/modules/4.10.0-42-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.60
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     7E15A641541A01799F6564A
depends:        
vermagic:       4.10.0-42-generic SMP mod_unload 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)
```

> cat /etc/ndiswrapper.conf
```
cat: /etc/ndiswrapper.conf: No such file or directory
```

> dkms status
```
ndiswrapper, 1.60, 4.10.0-42-generic, x86_64: installed
```

---

