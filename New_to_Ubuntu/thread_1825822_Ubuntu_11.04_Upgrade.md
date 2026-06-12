---
title: "Ubuntu 11.04 Upgrade"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by JadenRosen on 2011-08-15
Hello everybody!

I just updated my Ubuntu 10.10 to 11.04 the other day. And unfortunately when I boot into the default desktop (Ubuntu), the desktop environment is still GNOME 2.0 instead of Unity.

Is there something I have to do to switch it to Unity?

Thank's for the help :KS

---

### Post by fcomstoc on 2011-08-15
When you are at the login screen can you select Unity at the bottom of the screen (I think it says unity, I am not sure though)

This is the same way that you can select other environments like XFCE or KDE

---

### Post by mikewhatever on 2011-08-15
No, there is nothing to do. If you had the compatible hardware, the Unity interface would have loaded itself.

---

### Post by alphacrucis2 on 2011-08-15
> **JadenRosen said:**
> Hello everybody!

I just updated my Ubuntu 10.10 to 11.04 the other day. And unfortunately when I boot into the default desktop (Ubuntu), the desktop environment is still GNOME 2.0 instead of Unity.

Is there something I have to do to switch it to Unity?

Thank's for the help :KS

Unity requires 3D graphics. What graphics card do you have.

---

### Post by JadenRosen on 2011-08-16
Not sure which one it is...


josie@ubuntu:~/Desktop$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 02)
01:07.0 USB Controller: OPTi Inc. 82C861 (rev 10)
01:0b.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
01:0b.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
01:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)

Hope this has the right info...

---

### Post by Paqman on 2011-08-16
> **alphacrucis2 said:**
> Unity requires 3D graphics. What graphics card do you have.

There is also a [2D version of Unity](apt:unity-2d-default-settings) that's available if your graphics card isn't up to the job

---

### Post by Derek Topping on 2011-08-16
If you go to the additional drivers you should get a download that will do the trick

---

### Post by Paqman on 2011-08-16
> **Derek Topping said:**
> If you go to the additional drivers you should get a download that will do the trick

Intel graphics are normally bundled in with the kernel, I'm not aware of any that require a separate driver.

---

