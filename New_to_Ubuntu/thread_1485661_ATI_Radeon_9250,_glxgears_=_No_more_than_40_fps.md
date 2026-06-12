---
title: "ATI Radeon 9250, glxgears = No more than 40 fps"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by LeDechaine on 2010-05-17
```
ledechaine@QuadDamage:~$ glxgears
198 frames in 5.0 seconds = 39.521 FPS
198 frames in 5.0 seconds = 39.473 FPS
197 frames in 5.0 seconds = 39.394 FPS
198 frames in 5.0 seconds = 39.465 FPS
198 frames in 5.0 seconds = 39.408 FPS

```
I'm guessing this is not normal, assuming that only amsn and gajim were running in the background, even for a Pentium 3 866, with this kind of card.

And i'm guessing zsnes and some hd videos would stop lagging if I could fix this. ;)

Maybe this info can help:
```
$ uname -a
Linux QuadDamage 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux
```
(Jaunty)

(lshw)
```
*-display UNCLAIMED
                description: VGA compatible controller
                product: RV280 [Radeon 9200 PRO]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm bus_master cap_list
                configuration: latency=64 mingnt=8
```

(lspci)
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
```

(glxinfo)
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
(...)
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.4
OpenGL shading language version string: 1.20
```
(xorg.conf)
```
Section "Device"
        Identifier      "Configured Video Device"
EndSection
```

And this weird thing at the end of dmesg:
```
[   35.676381] [drm] Initialized drm 1.1.0 20060810
[   35.753849] radeon: disagrees about version of symbol drm_open
[   35.753866] radeon: Unknown symbol drm_open
[   35.754184] radeon: disagrees about version of symbol drm_fasync
[   35.754189] radeon: Unknown symbol drm_fasync
[   35.754510] radeon: disagrees about version of symbol drm_poll
[   35.754515] radeon: Unknown symbol drm_poll
[   35.754829] radeon: disagrees about version of symbol drm_get_resource_len
[   35.754835] radeon: Unknown symbol drm_get_resource_len
[   35.755256] radeon: disagrees about version of symbol drm_core_get_reg_ofs
[   35.755262] radeon: Unknown symbol drm_core_get_reg_ofs
[   35.755782] radeon: disagrees about version of symbol drm_irq_uninstall
[   35.755788] radeon: Unknown symbol drm_irq_uninstall
[   35.756274] radeon: disagrees about version of symbol drm_ioctl
[   35.756281] radeon: Unknown symbol drm_ioctl
[   35.756602] radeon: disagrees about version of symbol drm_exit
[   35.756607] radeon: Unknown symbol drm_exit
[   35.756920] radeon: disagrees about version of symbol drm_getsarea
[   35.756925] radeon: Unknown symbol drm_getsarea
[   35.764256] radeon: disagrees about version of symbol drm_core_ioremapfree
[   35.764270] radeon: Unknown symbol drm_core_ioremapfree
[   35.764593] radeon: disagrees about version of symbol drm_core_get_map_ofs
[   35.764599] radeon: Unknown symbol drm_core_get_map_ofs
[   35.764913] radeon: disagrees about version of symbol drm_init
[   35.764918] radeon: Unknown symbol drm_init
[   35.765230] radeon: disagrees about version of symbol drm_addmap
[   35.765235] radeon: Unknown symbol drm_addmap
[   35.765771] radeon: disagrees about version of symbol drm_get_resource_start
[   35.765777] radeon: Unknown symbol drm_get_resource_start
[   35.766091] radeon: disagrees about version of symbol drm_handle_vblank
[   35.766097] radeon: Unknown symbol drm_handle_vblank
[   35.766440] radeon: disagrees about version of symbol drm_ati_pcigart_init
[   35.766446] radeon: Unknown symbol drm_ati_pcigart_init
[   35.766786] radeon: disagrees about version of symbol drm_vblank_init
[   35.766791] radeon: Unknown symbol drm_vblank_init
[   35.767102] radeon: disagrees about version of symbol drm_rmmap
[   35.767108] radeon: Unknown symbol drm_rmmap
[   35.767533] radeon: disagrees about version of symbol drm_core_ioremap_wc
[   35.767538] radeon: Unknown symbol drm_core_ioremap_wc
[   35.767853] radeon: disagrees about version of symbol drm_mmap
[   35.767858] radeon: Unknown symbol drm_mmap
[   35.768523] radeon: disagrees about version of symbol drm_ati_pcigart_cleanup
[   35.768531] radeon: Unknown symbol drm_ati_pcigart_cleanup
[   35.768974] radeon: disagrees about version of symbol drm_core_reclaim_buffers
[   35.768980] radeon: Unknown symbol drm_core_reclaim_buffers
[   35.769337] radeon: disagrees about version of symbol drm_release
[   35.769342] radeon: Unknown symbol drm_release
```

**NOTE: This may have something to do with my now unrecognised 1280x1024 resolution (?). Added a line in xorg.conf to set it to 1280x1024, maybe because of a broken VGA wire.**

---

### Post by anewguy on 2010-05-17
I have the same video card except my latency shows as 32.  I have a slightly different system - AMD Athlon 64 3200+.  My glxgears show as:

dave@dave-desktop:~$ glxgears
4081 frames in 5.0 seconds
4274 frames in 5.0 seconds
4278 frames in 5.0 seconds
4274 frames in 5.0 seconds


One difference I am aware of that may make a difference:  I'm using 10.04, but this has been working for several releases now.  I have done nothing with xorg in 9.10 or 10.04 (it all works different anyway) and just let the system figure everything out automatically.  

If you go to System/Preferences/Monitor does it show your monitor by name and model?  If your monitor is not being recognized that would cause problems with available resolutions.  Since you mention you are messing with xorg.conf, have you also specified the refresh rates?

I personally would recommend updating to at least 9.10, if not just 10.04, and let the system figure it out for you - no xorg.conf needed or present.

Dave ;)

---

### Post by LeDechaine on 2010-05-17
Yeah well I vaguely remember seeing thousand(s) frames per second on 7.10 with the exact same machine...

I fixed xorg.conf by adding a "1280x1024" scancodes line since my monitor stopped being recognised. That's not the problem, I was just wondering if THIS could have affected my fps or even "disabled" my 3D card.

And I don't want to upgrade.
Upgrading to fix simple-ish things is like telling me "this car is just scrap, go buy another one" when the only thing not working right is the CD player or whatever...

I'll keep 9.04 for 10 years or more if I can, unless I get a new computer.

---

### Post by anewguy on 2010-05-17
> **LeDechaine said:**
> Yeah well I vaguely remember seeing thousand(s) frames per second on 7.10 with the exact same machine...

I fixed xorg.conf by adding a "1280x1024" scancodes line since my monitor stopped being recognised. That's not the problem, I was just wondering if THIS could have affected my fps or even "disabled" my 3D card.

And I don't want to upgrade.
Upgrading to fix simple-ish things is like telling me "this car is just scrap, go buy another one" when the only thing not working right is the CD player or whatever...

I'll keep 9.04 for 10 years or more if I can, unless I get a new computer.

Just trying to help.....if you don't want suggestions, don't ask.

Since you've made changes to xorg.conf and apparently are still missing things, post your entire xorg.conf here so we can see it.

---

### Post by MartyBuntu on 2010-05-17
40 FPS sounds pretty good, actually.

It's not the most powerful card in the world...

---

### Post by quadproc on 2010-05-17
The rate of 40 FPS sounds about right for the open source driver.  There is one more section of your xorg.conf file that we need: please type the following into a terminal and let us know the result
```
grep "river" < /etc/X11/xorg.conf
```
This will tell us which driver is actually in use.

quadproc

---

### Post by LeDechaine on 2010-05-18
Here is my entire (and small) xorg.conf.

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Acer AL1916"
	Modeline	"1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Acer AL1916"
	Monitor		"Acer AL1916"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	1280 1024
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```

---

### Post by QIII on 2010-05-18
I have an  on-board card on this machine.  It's an HD, so a bit newer than your legacy card.

Just for giggles, I switched to metacity and used Catalyst Control Center to drop "Wait for vertical refresh" to "Performance".  Got this

```
13499 frames in 5.0 seconds
14390 frames in 5.0 seconds
14400 frames in 5.0 seconds
14397 frames in 5.0 seconds
14401 frames in 5.0 seconds
14866 frames in 5.0 seconds
16115 frames in 5.0 seconds
16111 frames in 5.0 seconds
16093 frames in 5.0 seconds
```

When I changed it back to "Quality", I got this:

```
303 frames in 5.0 seconds
301 frames in 5.0 seconds
301 frames in 5.0 seconds
300 frames in 5.0 seconds
301 frames in 5.0 seconds
300 frames in 5.0 seconds
300 frames in 5.0 seconds
```

I'm not sure if you can even get the right Catalyst Control Center for that card (and the driver is legacy anyway), but fiddling around with that might be enlightening.

---

### Post by mastablasta on 2010-05-18
> **MartyBuntu said:**
> 40 FPS sounds pretty good, actually.
 
It's not the most powerful card in the world...
 
 
Actually i would like to know what's the big deal since the human eye can only catch 24 or is it 25 frames per second... So everything arround steady 30 is fine by me :-)

---

### Post by LeDechaine on 2010-05-18
> **mastablasta said:**
> Actually i would like to know what's the big deal since the human eye can only catch 24 or is it 25 frames per second... So everything arround steady 30 is fine by me :-)

Yeah right, try playing quake live with a system that only gets glxgears to 40 fps and your human eyes won't be pleased of the result.

I've just tried quake live which already ran flawlessly @ more than 30fps with this same system and I get an average of 0fps. Yes, **zero**. Let me guess: My 3D card is "off".

According to synaptic the radeon drivers are installed.
Looks like ubuntu took the privilege to **** up everything again without my consent.

---

### Post by QIII on 2010-05-18
mastablasta -- Actually, the human eye can distinguish about 60 fps --  hard to say, though, since human vision is analog.

Problem with 60 fps is screen artifacts during fast motion.  You can  definitely see that.

LeDechain:

 I don't think Ubuntu took the opportunity to **** up your system  without your consent.    That's not diagnostic.  It's frustration.

You said you may have a broken VGA wire and that you had changed your  xorg.conf to compensate.  That was in bold in your first post.  

If you do have a broken VGA wire, nothing you do in the OS will change the behavior.  

Diagnose.  Don't assume.  The change in behavior may be coincidental to a change in the OS.  "Post  Hoc Ergo Propter Hoc" is a logical fallacy.

Do you have another cable?  Another monitor?  Can you replace your current hardware with a known working cable or monitor?  Can you replace your card with a known working card.

Hardware breaks.  Cards, cables and monitors do not last forever.  Before you blame the OS (be that Windows, Linux or Unix), you need to eliminate hardware failure as the source of the problem.

Furthermore, as I said, you can change the frame rate by making  adjustments through Catalyst Control Center.

---

### Post by clhsharky on 2010-05-18
HI


glxgears
[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

> OpenGL renderer string: Software Rasterizer
Is always slow at rendering 3D.

dmesg shows drm mismatch.


Sharky

---

### Post by LeDechaine on 2010-05-18
I don't think I have the Catalyst control center since I use the radeon driver, I don't have xorg-driver-fglrx.

"Post Hoc Ergo Propter Hoc" is a logical fallacy.
Well, I think **because** of a broken VGA wire, **this** is now showing in the xorg.log:

```
drmOpenDevice: node name is /dev/dri/card0
[drm] failed to load kernel module "radeon"
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=262144K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 1280x1024
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
**(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf**
```

And since my screen has then stopped being recognised by ubuntu, it goes back to an ugly resolution by default, **with** 3D acceleration. But if I force it to 1280x1024, no 3D.

Sounds stupid, but that's what the xorg.log tells me.
Whatever, there may be no 3D acceleration at all with the ugly, lower resolution anyway. I'll just try to get another wire, hoping this will fix the problem.

---

### Post by QIII on 2010-05-18
> **LeDechaine said:**
> 
Well, I think **because** of a broken VGA wire, **this** is now showing in the xorg.log:


Seems to me that would qualify as a hardware issue.

---

### Post by LeDechaine on 2010-05-19
Agreed, i'll get another cable.

---

