---
title: "graphic/image problems ubuntu"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by Rpdiddy on 2010-08-20
Ok i have Lucid installed and ever since i've been experiencing image/ graphic problems
the panel shutdown button would look weird and disoriented. In firefox some images also become messed up. And im not sure if this corresponds with this but my computer sometimes just freezes out of the blue. The only way to restore it is by doing a hard reboot. Any ideas or help would be appreciated! 
EDIT: ubuntu 1.04
kernel linux 2.6.32-24-generic
memory 1 GB
processor Intel(R) Pentimum(R) D CPU 2.80GHz
ATI Radeon Xpress 200

EDIT- hwinfo
21: PCI 105.0: 0300 VGA compatible controller (VGA)             
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1002_5a61
  Unique ID: ul7N.dFXV26GrjA4
  Parent ID: vSkL.dQFUNbiC_g9
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:05.0
  SysFS BusID: 0000:01:05.0
  Hardware Class: graphics card
  Model: "ATI Radeon XPRESS 200 5A61 (PCIE)"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x5a61 "Radeon XPRESS 200 5A61 (PCIE)"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x2a3d 
  Driver: "radeon"
  Driver Modules: "drm"
  Memory Range: 0xd0000000-0xdfffffff (rw,prefetchable)
  I/O Ports: 0xd000-0xdfff (rw)
  Memory Range: 0xfeaf0000-0xfeafffff (rw,non-prefetchable)
  Memory Range: 0xfeac0000-0xfeadffff (ro,prefetchable,disabled)
  IRQ: 17 (34899 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001002d00005A61sv0000103Csd00002A3Dbc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: radeon
  Driver Info #1:
    XFree86 v4 Server Module: fglrx
    3D Support: yes
    Extensions: dri
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #10 (PCI bridge)

Primary display adapter: #21

---

### Post by mörgæs on 2010-08-20
It is a difficult screen card, as it is not supported any more. Please post the output from 

```
hwinfo --gfx
```

---

### Post by Vrroom on 2010-08-20
Go to preferences > monitors.
Check your refresh rate and take a note of it.
Now go to preferences > CompizConfig settings manager
Click on general settings. Then go to display settings.
Uncheck detect refresh rate.
Enter your refresh rate value.

You won't have problems any more.

---

### Post by Rpdiddy on 2010-08-22
ok i did post the hwinfo

---

### Post by mörgæs on 2010-08-22
As mentioned earlier this card is difficult. 

For most ATI cards there are two drivers available: The open source 'radeon' driver and the closed source 'fglrx'. However, the Xpress 200 is unsupported from the company under Ubuntu 10.04, so in this case there is only the radeon driver. 

I can not give a clear answer, since I have not tried the card myself, but googling gives several good posts, for example

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[http://ubuntuforums.org/showthread.php?t=1496254](http://ubuntuforums.org/showthread.php?t=1496254)
[http://ubuntuforums.org/showthread.php?t=1475045](http://ubuntuforums.org/showthread.php?t=1475045)

If you begin experimenting, it is probably best to post in the latter thread.

If you are ready for even more experimenting, you could give 10.10 (alpha) a try. You know the warnings: It is a version in development, and it changes without notice and so on.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

