---
title: "help with my VGA driver"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by toughengineer on 2010-06-01
# hwinfo --gfxcard
27: PCI 105.0: 0300 VGA compatible controller (VGA)             
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1002_791e
  Unique ID: ul7N.W_wkJ1GBuo3
  Parent ID: vSkL.HjQnVRFuoa8
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:05.0
  SysFS BusID: 0000:01:05.0
  Hardware Class: graphics card
  Model: "Micro-Star International K9AG Neo2"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x791e "RS690 [Radeon X1200 Series]"
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd."
  SubDevice: pci 0x7327 "K9AG Neo2"
  Driver: "radeon"
  Driver Modules: "drm"
  Memory Range: 0xf0000000-0xf7ffffff (rw,prefetchable)
  Memory Range: 0xfeaf0000-0xfeafffff (rw,non-prefetchable)
  I/O Ports: 0xd000-0xdfff (rw)
  Memory Range: 0xfe900000-0xfe9fffff (rw,non-prefetchable)
  IRQ: 26 (942747 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001002d0000791Esv00001462sd00007327bc03sc00i00"
  Driver Info #0:
    Driver Status: radeon is active
    Driver Activation Cmd: "modprobe radeon"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #9 (PCI bridge)

Primary display adapter: #27
root@ahmed-desktop:/usr/share/ati# dpkg-reconfigure -phigh xserver-xorg
root@ahmed-desktop:/usr/share/ati#  lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]


this is my VGA card .. i got the installation package from AMD and i install successfully and when i type in my terminal 

# aticonfig
Unable to open /etc/ati/control, please reinstall the driver.
aticonfig: No supported adapters detected


and my desktop effects are none now and the pc is extremely slow 
any help with that ?!

---

### Post by toughengineer on 2010-06-01
just forgot to say that in my AMD manual these packages are recommended and i don't have them 

XFree86-Mesa-libGL
XFree86-libs

and i can't find my xorg.conf in /etc/X11 
i am using ubuntu 10.04 lucid 
these are all the details ..
waiting for ur ideas ;)

---

