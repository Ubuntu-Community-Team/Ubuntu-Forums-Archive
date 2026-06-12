---
title: "Nvidia graphics &amp; Lucid: Low Res"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by bpowell2005 on 2010-05-03
Hello,

I've just upgraded from Jaunty - Karmic - Lucid. The upgrade seemed to go well, however, whenever I reboot, I get an error saying Ubuntu is in Low Res mode. The laptop boots find, and my desktop is the usual size 1366/768 however, I can't enable my Desktop Cube or advanced effects.

I go to System > Admin > hardware drivers, and ubuntu says no hardware drivers are enabled (and I don't have the option to chose any).

Help please!

Here is output from LSPCI and GLXinfo

LSPCI:

```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 16)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100


```

and glxinfo

```

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault


```

Note the seg-fault after the glxinfo...this concerns me.

Thanks everybody for any help you can provide.

---

### Post by jfreak_ on 2010-05-04
try removing your installed nvidia packages, and install the 19* nvidia packages, then run hardware drivers

---

### Post by bpowell2005 on 2010-05-04
> **jfreak_ said:**
> try removing your installed nvidia packages, and install the 19* nvidia packages, then run hardware drivers

Hi.

Well, the title of this thread is misleading (my fault)...I have an Intel M4 graphics chipset, not Nvidia...but it was working find under jaunty...not sure what gives now.

---

### Post by bpowell2005 on 2010-05-04
Hey all,

My problem may be 80% solved for the moment...as I mentioned earlier, I have an Intel M4 graphics chipset that's been working for me with Compiz before my upgrade to Lucid...

Somewhere during the lucid upgrade, Nvidia drivers were automatically installed, and these were messing me up!

So, a quick
```
sudo apt-get --purge remove nvidia*
```
Then a reboot, and I'm able to have desktop effects again, cube, water, the whole 9 yards!

I think there might still be a flicker once every 5 minutes or so, but I'm hopeful that'll be resolved in updates...it doesn't bug me as much as the lack of desktop effects.

I think I may have lost my fancy ubuntu boot up splash, but again, to me, that's a small price to pay.

---

### Post by -humanaut- on 2010-05-04
I'm rather confused here? The only default nvidia driver installed is Nouveau which is compatible with KMS settings you could have simple set it to not load instead of purging files.

---

### Post by rowinggolfer on 2010-05-05
this affected me too... on my acer 1810tz

---

### Post by bpowell2005 on 2010-05-05
> **rowinggolfer said:**
> this affected me too... on my acer 1810tz

Rowinggolfer: How did you solve the issue?

---

### Post by bpowell2005 on 2010-05-05
> **-humanaut- said:**
> I'm rather confused here? The only default nvidia driver installed is Nouveau which is compatible with KMS settings you could have simple set it to not load instead of purging files.

I think we'll just have to agree to disagree. The Nvidia drivers were certainly there, and not installed by me. Removing them has cleared my problem up.

---

### Post by rowinggolfer on 2010-05-08
> **bpowell2005 said:**
> Rowinggolfer: How did you solve the issue?

using the sudo apt-get --purge remove nvidia* method you recommended, many thanks.

BTW - I think this is a major bug, couldn't find it on launchpad though... and it's VERY difficult to describe

---

### Post by kwek on 2010-06-04
Woo.. thanks!  Removing the nvidia* packages solved it for me. I first noticed that I couldnt start XBMC because it said  something like "Missing OpenGL support" and in console: Error: couldn't find RGB GLX visual or fbconfig  My card from lspci:  00:02.1 Display controller [0380]: Intel Corporation 82G33/G31 Express Integrated Graphics Controller [8086:29c3] (rev 02)

---

