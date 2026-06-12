---
title: "i hate mesa3d, about fglrx"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by arli on 2006-12-17
i install the 'xorg-driver-fglrx' version '7.1.0-8.32.5+2.6.20.1-2' follow  'Method 1' of [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

but

```

[COLOR="Blue"]arli@alx-u7:~$ fglrxinfo[/COLOR]

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

[COLOR="Blue"]arli@alx-u7:~$ glxinfo | grep render[/COLOR]

direct rendering: No
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: Mesa GLX Indirect

[COLOR="Blue"]arli@alx-u7:~$ xvinfo[/COLOR]

X-Video Extension version 2.2
screen #0
 no adaptors present

```

```

[COLOR="Blue"]arli@alx-u7:~$ sudo lshw | grep X1600[/COLOR]

                product: M56P [Radeon Mobility X1600]

```

```

[COLOR="Blue"]arli@alx-u7:~$ lsmod | grep fglrx[/COLOR]

fglrx                 415052  0 
agpgart                34888  2 fglrx,intel_agp

```

```

[COLOR="Blue"]arli@alx-u7:~$ dmesg | grep fglrx[/COLOR]

[   21.008000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   21.008000] [fglrx] Maximum main memory to use for locked dma buffers: 1898 MBytes.
[   21.008000] [fglrx] module loaded - fglrx 8.31.5 [Nov  9 2006] on minor 0
[COLOR="Red"][   23.352000] [fglrx:firegl_unlock] *ERROR* Process 4658(XORG) using kernel context 0[/COLOR]

```

```

[COLOR="Blue"]arli@alx-u7:~$ sudo dmesg | grep CPU[/COLOR]

[   21.792326] Initializing CPU#0
[   21.964343] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000
[   21.964362] CPU: L1 I cache: 32K, L1 D cache: 32K
[   21.964366] CPU: L2 cache: 2048K
[   21.964370] CPU: Hyper-Threading is disabled
[   21.964373] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00000940 0000c189 00000000 00000000
[   22.608406] CPU0: Intel Genuine Intel(R) CPU           T2300  @ 1.66GHz stepping 08
[   22.619225] Initializing CPU#1
[   22.699067] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000
[   22.699076] CPU: L1 I cache: 32K, L1 D cache: 32K
[   22.699078] CPU: L2 cache: 2048K
[   22.699080] CPU: Hyper-Threading is disabled
[   22.699082] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00000940 0000c189 00000000 00000000
[   22.699536] CPU1: Intel Genuine Intel(R) CPU           T2300  @ 1.66GHz stepping 08
[   22.846852] checking TSC synchronization across 2 CPUs: passed.
[    0.003992] Brought up 2 CPUs
[    0.838309] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [   AMI] OemTableId [  CPU1PM] [20060707]
[    0.839466] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    0.839979] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.840864] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [   AMI] OemTableId [  CPU2PM] [20060707]
[    0.841965] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    0.842477] ACPI: Processor [CPU2] (supports 8 throttling states)

```

```

[COLOR="Blue"]arli@alx-u7:~$ cat /proc/version[/COLOR]

Linux version 2.6.19-7-generic (root@vernadsky) (gcc version 4.1.2 20061115 (prerelease) (Ubuntu 4.1.1-20ubuntu1)) #2 SMP Mon Dec 4 16:46:19 UTC 2006 (Ubuntu 2.6.19-7.11-generic)

```

```

[COLOR="Blue"]arli@alx-u7:~$ cat /etc/X11/xorg.conf[/COLOR]

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
	Option	    "SHMConfig" "on"
	Option	    "touchpadoff" "1"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```

but, be no problem when me make install of ATI official 8.32.5 drviers(follow  'Method 2' of [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")
), but edgy mode..

help me .... pls ... is toooo big problem for me, because my job need 3d ....

---

### Post by Rackerz on 2006-12-17
Have you tried opening up the package manager installing 'fglrx' and then changing 'ati' to 'fglrx' in your xorg.conf?

---

### Post by arli on 2006-12-17
> **Rackerz said:**
> Have you tried opening up the package manager installing 'fglrx' and then changing 'ati' to 'fglrx' in your xorg.conf?

y, see above. about tag: 'arli@alx-u7:~$ cat /etc/X11/xorg.conf'

i think is 'feisty' or 'the driver from Synaptic sources' problem.

so i want try official driver but i can't make by 'feisty' mode:

```

[COLOR="Blue"]arli@alx-u7:~/D6/Software$ bash ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/feisty[/COLOR]

Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.32.5........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/feisty
[COLOR="Red"]Requested package is not supported.[/COLOR]
Removing temporary directory: fglrx-install

```

---

