---
title: "Enabling USB In VM Ware"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by twinaxel on 2009-07-21
Hi Been experimenting with VM managed to get it running XP 
but don't have USB support is this an easy fix?

The OS is Jaunty thanks for any replys.

---

### Post by swoll1980 on 2009-07-21
It should be automatic on vmware. It might have to be enabled when the vm is created, I don't remember. VirtualBox won't give you the usb support unless you download the non free version from Sun.com

---

### Post by JKyleOKC on 2009-07-21
> **twinaxel said:**
> Hi Been experimenting with VM managed to get it running XP 
but don't have USB support is this an easy fix?

The OS is Jaunty thanks for any replys.

Be sure you have the VMWare Tools package installed in your XP VM. Then go to full screen display mode and at the top you should see a sort of task bar that includes a pulldown option for "Devices." Pull it down and you should see your USB devices listed. Highlight the one you want to use and get a fly-out menu allowing you to connect to it. Click on "connect" and you should soon see XP going through its "new device detected" routines to make the USB device active.

Before you exit the XP VM, be sure to go to the pulldown and disconnect the USB device if it's a flash drive. Otherwise it's possible that XP's delayed write "feature" can destroy it.

---

