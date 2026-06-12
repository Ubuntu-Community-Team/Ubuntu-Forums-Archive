---
title: "Why does FretsOnFire work faster on Ubuntu then on Arch??"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by pluckypigeon on 2009-01-25
Frets on Fire worked fine on Ubuntu with Gnome but is incredibly slow with Arch and Openbox.

Any ideas why?

Thanks in advance!

---

### Post by pluckypigeon on 2009-01-25
A Bit more info:

Graphics:
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

Arch:

```
Section "Device"
	Identifier "intelchip"
	Driver "intel"
	BusID "PCI:0:2:0"
#	VideoRam 64000
#	Option "DRI" "off"
   	Option "NoAccel"
	Option "DPI" "96 x 96"
	Option "UseEdidDpi" "false"
#	Option "AccelMethod" "xaa"
#	Option "XAANoOffscreenPixmaps" "on"
#	Option "AccelMethod" "exa"
#	Option "MigrationHeuristic" "smart"
	Option "MigrationHeuristic" "greedy"
#	Option "FramebufferCompression" "on"
#	Option "Tiling" "on"
	Option "ExaNoComposite" "false"
EndSection
```
Ubuntu:

```
Section "Device"
	Identifier	"Configured Video Device"


```

---

### Post by kavon89 on 2009-01-25
> Option "NoAccel"

Looks interesting


run glxgears on both systems for 15 seconds and compare the average fps.

---

### Post by pluckypigeon on 2009-01-25
> **kavon89 said:**
> Looks interesting


run glxgears on both systems for 15 seconds and compare the average fps.

If I enable acceleration X crashes with no screens. 

Arch:

415 frames in 5.0 seconds = 82.828 FPS
429 frames in 5.0 seconds = 85.618 FPS
425 frames in 5.0 seconds = 84.992 FPS
= 84.4793 FPS


Ubuntu:

828 frames in 5.0 seconds = 165.505 FPS
864 frames in 5.0 seconds = 172.673 FPS
795 frames in 5.0 seconds = 158.900 FPS
= 165.6926 FPS

Any ideas?

---

### Post by kavon89 on 2009-01-25
That is a very crappy FPS for a desktop. Here is what mine is with properly installed nvidia drivers and dual monitor resolution.

```
kavon@kavon-r61:~$ glxgears
10881 frames in 5.0 seconds = 2173.384 FPS
11165 frames in 5.0 seconds = 2232.980 FPS
11119 frames in 5.0 seconds = 2221.585 FPS
11094 frames in 5.0 seconds = 2218.540 FPS

```

---

