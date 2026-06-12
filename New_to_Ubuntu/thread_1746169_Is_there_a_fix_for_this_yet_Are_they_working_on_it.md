---
title: "Is there a fix for this yet? Are they working on it?"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by jrozo17 on 2011-05-01
Ok so a few weeks ago i upgraded from 10.10 to 11.04, during beta 2. I experienced quite a few problems, one of them being system crashes which didn't happen before.

Today I totally wiped out my hard drive and just installed a fresh copy of 11.04 hoping it would solve all the problems. Well I STILL have crashes randomly, and I don't think I'm alone. 

I attached a pic of what keeps showing up..

So my main question is, is the Ubuntu team actually working on this? How long is it going to take? And why did they release an OS that doesn't even seem finished?(bug wise)
Anyone else experiencing this?

---

### Post by dniMretsaM on 2011-05-01
Is that lines of code or just white lines?

---

### Post by TeoBigusGeekus on 2011-05-01
Are you using nvidia?

---

### Post by jrozo17 on 2011-05-01
> **dniMretsaM said:**
> Is that lines of code or just white lines?

it's just horizontal lines everytime, sometimes different colors.

---

### Post by jrozo17 on 2011-05-01
> **TeoBigusGeekus said:**
> Are you using nvidia?

Im not sure. how do i check?

---

### Post by dniMretsaM on 2011-05-01
```
lspci
```

---

### Post by jrozo17 on 2011-05-01
> **dniMretsaM said:**
> ```
lspci
```

This is all it says.. so im guessing i dont have nvidea?

> **jrozo17 said:**
> ```
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
05:00.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
05:00.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
05:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 61)
05:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)

```

---

### Post by lykwydchykyn on 2011-05-01
> **jrozo17 said:**
> 
So my main question is, is the Ubuntu team actually working on this? How long is it going to take? And why did they release an OS that doesn't even seem finished?(bug wise)
Anyone else experiencing this?

Have you made them aware of the problem?
One can only assume that they released the OS because 
 - they didn't see such a problem during beta testing
 - Nobody reported it during beta testing
 - It's due to things beyond their control (hardware bugs, proprietary drivers, etc)

Please, let's give the developers the benefit of the doubt here...

---

### Post by jrozo17 on 2011-05-01
> **lykwydchykyn said:**
> Have you made them aware of the problem?
One can only assume that they released the OS because 
 - they didn't see such a problem during beta testing
 - Nobody reported it during beta testing
 - It's due to things beyond their control (hardware bugs, proprietary drivers, etc)

Please, let's give the developers the benefit of the doubt here...

Good point, but why would all older versions of Ubuntu work well with my hardware and this one wont? I hope there isnt no solution. Also, I'm not sure how to report a bug like this since my computer freezes. :confused:

---

### Post by dniMretsaM on 2011-05-01
> **jrozo17 said:**
> This is all it says.. so im guessing i dont have nvidea?

Nope, you have an Intel graphics card. Not NVIDIA.

---

### Post by lykwydchykyn on 2011-05-01
> **jrozo17 said:**
> This is all it says.. so im guessing i dont have nvidea?

Nope, you have an intel 915 chip, for future reference.  Older intel chips like this can require some tweaking to get working right.

can you post the output from:
```

grep -i driver /var/log/Xorg.0.log
grep EE /var/log/Xorg.0.log

```

That will show what driver it's trying to use, and if it's encountering any errors.

---

### Post by TeoBigusGeekus on 2011-05-01
I have freezes like this in lucid and maverick due to nvidia restricted drivers (I am not touching natty). Uninstalled them and the problem vanished.

Try to use the classic desktop for a while with the desktop effects disabled and see how it goes.

---

### Post by lykwydchykyn on 2011-05-01
> **jrozo17 said:**
> Good point, but why would all older versions of Ubuntu work well with my hardware and this one wont? I hope there isnt no solution. Also, I'm not sure how to report a bug like this since my computer freezes. :confused:

Xorg has been going through a lot of changes in the last few years, and the Intel driver as well.  IME support for older intel chips, unfortunately, seems to be getting worse.  I don't have anything with a 915, but I have some 845/855 devices, and they do very poorly with Natty.  

Are you logging in to Unity or ubuntu classic?

---

### Post by jrozo17 on 2011-05-01
> **lykwydchykyn said:**
> Nope, you have an intel 915 chip, for future reference.  Older intel chips like this can require some tweaking to get working right.

can you post the output from:
```

grep -i driver /var/log/Xorg.0.log
grep EE /var/log/Xorg.0.log

```That will show what driver it's trying to use, and if it's encountering any errors.


I have no idea how to make sense of this, sorry I'm still new to terminals.

james@james-desktop:~$ grep -i driver /var/log/Xorg.0.log
[    12.354]     X.Org Video Driver: 10.0
[    12.354]     X.Org XInput driver : 12.3
[    12.379] (==) Matched intel as autoconfigured driver 0
[    12.379] (==) Matched vesa as autoconfigured driver 1
[    12.379] (==) Matched fbdev as autoconfigured driver 2
[    12.379] (==) Assigned the driver to the xf86ConfigLayout
[    12.384] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    12.385]     Module class: X.Org Video Driver
[    12.385]     ABI class: X.Org Video Driver, version 10.0
[    12.386] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    12.386]     Module class: X.Org Video Driver
[    12.386]     ABI class: X.Org Video Driver, version 10.0
[    12.387] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    12.387]     ABI class: X.Org Video Driver, version 10.0
[    12.387] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
[    12.393] (II) VESA: driver for VESA chipsets: vesa
[    12.393] (II) FBDEV: driver for framebuffer: fbdev
[    12.400] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    12.401]     ABI class: X.Org Video Driver, version 10.0
[    12.705] (II) intel(0): [DRI2]   DRI driver: i915
[    12.705] (II) UXA(0): Driver registered support for the following operations:
[    12.762] (II) AIGLX: Trying DRI driver /usr/lib/dri/i915_dri.so
[    12.797]     Module class: X.Org XInput Driver
[    12.797]     ABI class: X.Org XInput driver, version 12.3
[    12.797] (II) Using input driver 'evdev' for 'Power Button'
[    12.806] (II) Using input driver 'evdev' for 'Sleep Button'
[    12.812] (II) Using input driver 'evdev' for 'Logitech USB RECEIVER'
[    12.813] (II) No input driver/identifier specified (ignoring)
[    12.823] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
james@james-desktop:~$ grep EE /var/log/Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.371] (II) Loading extension MIT-SCREEN-SAVER
james@james-desktop:~$

---

### Post by Blasphemist on 2011-05-01
This is from the document linked below.

> How do I know my GPU can run Unity?
There is a test program in Natty for that. Run this command: 

/usr/lib/nux/unity_support_test -p 

It will tell you if your system has the required capabilities for Unity. This is the same program we run at boot time to decide if Unity will be started or if a fall-back should run instead.

What drivers do you recommend?
AMD GPUs:

Fglrx driver: We have had some issues with the fglrx driver but we have been able to resolve them. With the fglrx driver, you will be missing features such as Kernel Mode Setting (KMS).
Open Source Radeon driver: can exhibit rendering artifacts on some systems. In the "System 3" configuration, Unity is not usable due to serious rendering issues.
NVidia GPUs: Nvidia propietary drivers.
Intel GPUs: Intel open source drivers.

This is what you can expect to see.

> jim@jim-Satellite-L505:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20100330 DEVELOPMENT x86/MMX/SSE2
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes


[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

---

### Post by jrozo17 on 2011-05-01
> **TeoBigusGeekus said:**
> I have freezes like this in lucid and maverick due to nvidia restricted drivers (I am not touching natty). Uninstalled them and the problem vanished.

Try to use the classic desktop for a while with the desktop effects disabled and see how it goes.

Thanks for the suggestion, I may try doing that.

---

### Post by jrozo17 on 2011-05-01
> **lykwydchykyn said:**
> Xorg has been going through a lot of changes in the last few years, and the Intel driver as well.  IME support for older intel chips, unfortunately, seems to be getting worse.  I don't have anything with a 915, but I have some 845/855 devices, and they do very poorly with Natty.  

Are you logging in to Unity or ubuntu classic?

Well thats a bummer. Im using Unity.

---

### Post by jrozo17 on 2011-05-01
> **Blasphemist said:**
> This is from the document linked below.



This is what you can expect to see.



[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)


Everything said yes, just as you said.

---

### Post by jrozo17 on 2011-05-01
Should I just wait it out and see if they fix this? I just use Ubuntu to surf the net anyway, so its not a huge problem for me. Just irritating at times.

---

### Post by Blasphemist on 2011-05-01
> **jrozo17 said:**
> Everything said yes, just as you said.

Did anything in the demystifying link help?

---

### Post by jrozo17 on 2011-05-01
> **Blasphemist said:**
> Did anything in the demystifying link help?

It gives useful information, but doesnt help tremendously. I did look at what they tested unity on though, will it matter that my computer is from 04? How far back does it support?

---

### Post by Blasphemist on 2011-05-01
There's no specific ancientness limit :) You're getting some darn good lifetime out of that.

Do you have any way that you know you can produce the issue? Are there any patterns to when this comes up? The more detail you can figure out, the higher the chance a solution can be found. Have you checked in launchpad for any known bug and workarounds that may have been found by others during testing? Try searches from this link and see what you can find. 

[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

On one of the rant threads someone reminded everyone that helping as a participating member of the community is really important. This is a chance to help yourself and others. Unfortunately I don't have an answer at this time.

---

### Post by lykwydchykyn on 2011-05-01
> **jrozo17 said:**
> I have no idea how to make sense of this, sorry I'm still new to terminals.

That's ok, the point is that other people here can make sense of it.

> 
james@james-desktop:~$ grep -i driver /var/log/Xorg.0.log
[    12.354]     X.Org Video Driver: 10.0
[    12.354]     X.Org XInput driver : 12.3
[    12.379] (==) Matched intel as autoconfigured driver 0
[    12.379] (==) Matched vesa as autoconfigured driver 1
[    12.379] (==) Matched fbdev as autoconfigured driver 2
[    12.379] (==) Assigned the driver to the xf86ConfigLayout
[    12.384] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    12.385]     Module class: X.Org Video Driver
[    12.385]     ABI class: X.Org Video Driver, version 10.0
[    12.386] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    12.386]     Module class: X.Org Video Driver
[    12.386]     ABI class: X.Org Video Driver, version 10.0
[    12.387] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    12.387]     ABI class: X.Org Video Driver, version 10.0
[    12.387] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
[    12.393] (II) VESA: driver for VESA chipsets: vesa
[    12.393] (II) FBDEV: driver for framebuffer: fbdev
[    12.400] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    12.401]     ABI class: X.Org Video Driver, version 10.0
[    12.705] (II) intel(0): [DRI2]   DRI driver: i915
[    12.705] (II) UXA(0): Driver registered support for the following operations:
[    12.762] (II) AIGLX: Trying DRI driver /usr/lib/dri/i915_dri.so
[    12.797]     Module class: X.Org XInput Driver
[    12.797]     ABI class: X.Org XInput driver, version 12.3
[    12.797] (II) Using input driver 'evdev' for 'Power Button'
[    12.806] (II) Using input driver 'evdev' for 'Sleep Button'
[    12.812] (II) Using input driver 'evdev' for 'Logitech USB RECEIVER'
[    12.813] (II) No input driver/identifier specified (ignoring)
[    12.823] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
james@james-desktop:~$ grep EE /var/log/Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.371] (II) Loading extension MIT-SCREEN-SAVER
james@james-desktop:~$

So there are no X errors, and it's using the proper (intel) driver.  Basically, Unity isn't going to happen on this hardware (yet).  Try classic, or some other desktop like XFCE.

---

### Post by jrozo17 on 2011-05-04
Thanks for all the help guys. After a few updates, everything seems fine. 
:guitar:

---

