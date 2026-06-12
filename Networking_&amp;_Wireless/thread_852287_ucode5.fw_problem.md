---
title: "ucode5.fw problem"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by gleble on 2008-07-07
I am trying(like everyone else,it seems) to get wireless running on Hardy. Below is an excerpt from the output of dmesg. I says it can't use ucode5.fw . However if you look at the code below, it has been extracted somewhere. Is it maybe in the wrong place?

```
[   49.358114] sky2 eth0: enabling interface
[   50.539135] [drm] Initialized drm 1.1.0 20060810
[   50.542532] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   50.542543] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   50.542628] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   58.634020] NET: Registered protocol family 10
[   58.634491] lo: Disabled Privacy Extensions
[   58.635035] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   59.204910] input: b43-phy0 as /devices/virtual/input/input13
[   59.267579] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   59.267588] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
```


```
neil@neil-laptop:/lib/firmware/broadcom-wl-4.80.53.0/kmod$ sudo /lib/firmware/b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
This file is recognised as:
  ID         :  FW11
  filename   :  wl_apsta.o
  version    :  351.126
  MD5        :  9207bc565c2fc9fa1591f6c7911d3fc0
Extracting b43/ucode4.fw
Extracting b43/ucode5.fw
Extracting b43/ucode11.fw
Extracting b43/ucode13.fw
Extracting b43/pcm4.fw
Extracting b43/pcm5.fw
Extracting b43/b0g0initvals4.fw
Extracting b43/b0g0bsinitvals4.fw
Extracting b43/a0g0initvals4.fw
Extracting b43/a0g0bsinitvals4.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/lp0initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/a0g1bsinitvals13.fw
neil@neil-laptop:/lib/firmware/broadcom-wl-4.80.53.0/kmod$ 



```
I'm hoping if I can resolve this wireless will work

---

### Post by chili555 on 2008-07-07
Did it extract to:```
/lib/firmware/b43/ucode5.fw
```Or elsewhere? Find out with:```
sudo updatedb
locate ucode5.fw
```*updatedb* will take a few moments, so please be patient.

---

### Post by gleble on 2008-07-07
No just lib/firmware . However, not sure why but I've got wireless up and running.

---

