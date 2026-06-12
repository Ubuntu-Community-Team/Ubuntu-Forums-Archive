---
title: "Issue with Nvidia 8800GTS and Intrepid"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by willis575 on 2008-12-11
I upgraded to 8.10 today and now I am stuck in low graphics mode. When I attempt to go into the Nvidia X-Server settings menu in Administration it tells me that I am not using the nvidia x driver and asks me to run nvidia-xconfig as root and restart the x server. However, when i run nvidia-xconfig it gives me a bunch of warnings and says that is unable to write to directory /etc/X11. I'm stuck!

---

### Post by mikewhatever on 2008-12-11
Have you checked if the restricted driver is enabled under System/Admin/Hardware Drivers? The error with nvidia-xconfig is probably related to the lack of admin privileges. It should be run as root, <sudo nvidia-xconfig>.

---

### Post by willis575 on 2008-12-11
> **mikewhatever said:**
> Have you checked if the restricted driver is enabled under System/Admin/Hardware Drivers? The error with nvidia-xconfig is probably related to the lack of admin privileges. It should be run as root, <sudo nvidia-xconfig>.

I ran the command using sudo with the same result. In restricted drivers it says that the Nvidia driver is active

---

### Post by mikewhatever on 2008-12-11
OK, how about <sudo dpkg-reconfigure -phigh xserver-xorg>.

---

### Post by willis575 on 2008-12-11
> **mikewhatever said:**
> OK, how about <sudo dpkg-reconfigure -phigh xserver-xorg>.

OK, I did that and restarted. Nvidia driver is still not running. Ran nvidia-xconfig and it told me "validation error: data incomplete in file /etc/X11/xorg.conf.backup device section "configured video device" must have a driver line. new X configuration file written to /etc/X11/xorg.conf


restarted computer and still in low graphics mode. By the way, in restricted drivers it says driver 177 is active.

Thanks for helping me buddy, I can usually find the answer somewhere on the forums but tonight I'm really stuck!

---

### Post by Hospadar on 2008-12-11
could you post "lsmod | grep nvidia"

Could you also post your xorg.conf file?

What happens when you run "sudo nvidia-settings" does it complain about drivers?

---

### Post by willis575 on 2008-12-11
[HTML]$ lsmod | grep nvidia
nvidia               3934028  0 
agpgart                34760  2 nvidia,intel_agp[/HTML]

sudo nvidia-settings gives me this

[HTML]You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. [/HTML]

---

### Post by mikewhatever on 2008-12-12
I wonder why xconfig complains that nvidia is not the driver in xorg.conf. Let's check if 177 is installed. <dpkg -s nvidia-glx-177>

---

### Post by willis575 on 2008-12-12
> **mikewhatever said:**
> I wonder why xconfig complains that nvidia is not the driver in xorg.conf. Let's check if 177 is installed. <dpkg -s nvidia-glx-177>

here it is.

silver@silver-desktop:~$ dpkg -s nvidia-glx-177
Package: nvidia-glx-177
Status: install ok installed
Priority: optional
Section: restricted/misc
Installed-Size: 25168
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: nvidia-graphics-drivers-177
Version: 177.82-0ubuntu0.1
Replaces: nvidia-glx, nvidia-glx-173, nvidia-glx-177, nvidia-glx-180, nvidia-glx-71, nvidia-glx-96, nvidia-glx-envy, nvidia-glx-legacy, nvidia-glx-legacy-envy, nvidia-glx-new, nvidia-glx-new-envy, nvidia-glx-src
Provides: nvidia-glx, xserver-xorg-video-4
Depends: nvidia-177-kernel-source (>= 177.82), x11-common (>= 1:7.0.0), libc6 (>= 2.1.3), libgcc1 (>= 1:4.1.1), libgl1-mesa | libgl1, libx11-6, libxext6, zlib1g (>= 1:1.1.4)
Recommends: nvidia-settings
Conflicts: nvidia-glx, nvidia-glx-src, xorg-driver-fglrx
Description: NVIDIA binary Xorg driver
 These binary drivers provide optimized hardware
 acceleration of  OpenGL applications via a direct-rendering X Server.
 AGP, PCIe, SLI, TV-out and flat panel displays are also supported.
 .
 Please see the nvidia-177-kernel-source package for building the kernel module
 required by this package. This will provide nvidia-kernel-<version>
 .
 The following GPUs are supported:
 GeForce 6800 Ultra, GeForce 6800, GeForce 6800 LE, GeForce
 6800 XE, GeForce 6800 XT, GeForce 6800 GT, GeForce 6800 GT,
 GeForce 6800 GS, GeForce 6800 XT, GeForce 7800 GTX, GeForce
 7800 GTX, GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI
 , GeForce Go 7800, GeForce Go 7800 GTX, GeForce 6800 GS, GeF
 orce 6800, GeForce 6800 LE, GeForce 6800 XT, GeForce Go 6800
 , GeForce Go 6800 Ultra, GeForce 6800, GeForce 6600 GT, GeFo
 rce 6600, GeForce 6200, GeForce 6600 LE, GeForce 7800 GS, Ge
 Force 6800 GS, GeForce 6800 Ultra, GeForce 6600 GT, GeForce
 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600, GeF
 orce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL, G
 eForce Go 6600, GeForce Go 6600 GT, GeForce 6200, GeForce 65
 00, GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(T
 M), GeForce 6200 LE, GeForce Go 6200, GeForce Go 6400, GeFor
 ce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 7100 GS,
 GeForce 8800 GTX, GeForce 8800 GTS, GeForce 8800 Ultra, Tesl
 a C870, GeForce 7350 LE, GeForce 7300 LE, GeForce 7300 SE/72
 00 GS, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400, Ge
 Force 7500 LE, GeForce 7300 GS, GeForce 6800, GeForce 6800 L
 E, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200, GeForce 6
 200 A-LE, GeForce 6150, GeForce 6150 LE, GeForce 6100, GeFor
 ce Go 6150, GeForce Go 6100, GeForce 7900 GTX, GeForce 7900
 GT/GTO, GeForce 7900 GS, GeForce 7950 GX2, GeForce 7950 GX2,
  GeForce 7950 GT, GeForce Go 7950 GTX, GeForce Go 7900 GS, G
 eForce Go 7900 GTX, GeForce 7600 GT, GeForce 7600 GS, GeForc
 e 7900 GS, GeForce 7950 GT, GeForce 7650 GS, GeForce 7600 GT
 , GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce
  7300 GT, GeForce Go 7600, GeForce Go 7600 GT, GeForce 6150S
 E nForce 430, GeForce 6100 nForce 405, GeForce 6100 nForce 4
 00, GeForce 6100 nForce 420, GeForce 8600 GTS, GeForce 8600
 GT, GeForce 8600 GT, GeForce 8400 GS, GeForce 9500M GS, GeFo
 rce 8600M GT, GeForce 8700M GT, GeForce 8400 SE, GeForce 850
 0 GT, GeForce 8400 GS, GeForce 8300 GS, GeForce 8400 GS, GeF
 orce 8600M GS, GeForce 8400M GT, GeForce 8400M GS, GeForce 8
 400M G, GeForce 9400 GT, GeForce 7150M / nForce 630M, GeForc
 e 7000M / nForce 610M, GeForce 7050 PV / NVIDIA nForce 630a,
  GeForce 7050 PV / NVIDIA nForce 630a, GeForce 7025 / NVIDIA
  nForce 630a, GeForce GTX 280, GeForce GTX 260, GeForce 8800
  GTS 512, GeForce 8800 GT, GeForce 9800 GX2, GeForce 8800 GS
 , GeForce 8800M GTS, GeForce 8800M GTX, GeForce 8800 GS, GeF
 orce 9600 GSO, GeForce 8800 GT, GeForce 9800 GTX, GeForce 96
 00 GT, GeForce 9600 GS, GeForce 9800M GTS, GeForce 9800M GTS
 , GeForce 9600M GT, GeForce 9600M GS, GeForce 9500M G, GeFor
 ce 9300 GS, GeForce 8400 GS, GeForce 9300M GS, GeForce 7150
 / NVIDIA nForce 630i, GeForce 7100 / NVIDIA nForce 630i, GeF
 orce 7050 / NVIDIA nForce 610i, GeForce 8300, GeForce 8200,
 nForce 730a, GeForce 8200, GeForce 8100 / nForce 720a, Quadr
 o FX 4000, Quadro FX 4500, Quadro FX Go1400, Quadro FX 3450/
 4000 SDI, Quadro FX 1400, Quadro FX 4400/Quadro FX 3400, Qua
 dro NVS 440, Quadro FX 540M, Quadro FX 550, Quadro FX 540, Q
 uadro NVS 285, Quadro FX 5600, Quadro FX 4600, Quadro NVS 11
 0M, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M, Quadro
  FX 350, Quadro NVS 210S / NVIDIA GeForce 6150LE, Quadro FX
 2500M, Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quad
 ro FX 1500, Quadro FX 4500 X2, Quadro FX 560, Quadro FX 370,
  Quadro NVS 320M, Quadro FX 570M, Quadro FX 1600M, Quadro FX
  570, Quadro FX 1700, Quadro NVS 140M, Quadro NVS 130M, Quad
 ro NVS 135M, Quadro FX 360M, Quadro NVS 290, Quadro FX 3700,
  Quadro FX 3600M
 .
 See /usr/share/doc/nvidia-glx/README.txt.gz for a complete list
 of supported GPUs and PCIIDs
 .
Original-Maintainer: Debian NVIDIA Maintainers <pkg-nvidia-devel@lists.alioth.debian.org>

---

### Post by willis575 on 2008-12-12
bump

---

### Post by willis575 on 2008-12-12
bump

---

### Post by phidia on 2008-12-12
There are problems with xorg in 8.10 
You upgraded-some people here would blame your problem on that saying you should do a clean install instead.
You might try to install envyng and use that to install the driver. If that doesn't work you may have to do a clean install.

---

### Post by willis575 on 2008-12-12
I have tried installing envy, however it doesn't show up in the menu at all. It says it is installed in synaptic, but I can't find it. Would reinstalling X work as opposed to a clean install? I've got a lot of data i would rather not lose.

---

### Post by willis575 on 2008-12-16
I'm here mikewhatever.... thanks again for helping me out buddy!

---

### Post by l1nuxb0x on 2008-12-16
I don't have an answer but I just wanted to interject that I have an 8800 gts and it's working perfectly, so things should work out for you. 

All I did was enable the restricted driver when it comes up on the first boot.

---

### Post by willis575 on 2008-12-16
I sure hope everything works out! Now my machine won't even turn on lol!

---

### Post by mikewhatever on 2008-12-16
> **willis575 said:**
> I sure hope everything works out! Now my machine won't even turn on lol!

Do you mean there is a power problem, a boot problem, or a black screen after boot?
Back to the original problem, I thought of trying to fix xserver through recovery mode (usually the second boot option). If you manage to turn the machine on, try selecting the recovery mode option at the boot menu, and then select 'Try to fix xserver' option.

---

### Post by willis575 on 2008-12-16
> **mikewhatever said:**
> Do you mean there is a power problem, a boot problem, or a black screen after boot?
Back to the original problem, I thought of trying to fix xserver through recovery mode (usually the second boot option). If you manage to turn the machine on, try selecting the recovery mode option at the boot menu, and then select 'Try to fix xserver' option.

After I got your email, I booted my machine up. Once at the desktop everything froze and I had to do a hard restart. However, power light comes on and I can hear the fans running, but the HDD light is off and no signal is going to the screen. Also, I tried "Try to fix xserver" option a few days ago to no avail. Hopefully I can get my machine back on... I'll pm you if I do...

---

### Post by fr0gg on 2009-04-30
Hey guys, I'm trying to get my 8800gts working as well..nothing happens when I try to activate the restricted drivers, it pops up with a small window saying "downloading and installing" but afterwards still says "Driver not activated" next the radio button. I've also tried going to the nvidia site: [http://www.nvidia.com/object/linux_display_ia32_180.51.html]("http://www.nvidia.com/object/linux_display_ia32_180.51.html"), but when I try and run ```
sh NVIDIA-Linux-x86-180.51-pkg1.run
``` I get```
sh: Can't open NVIDIA-Linux-x86-180.51.pkg1.run
```

What am I doing wrong? Any help would be much appreciated, thank you!

OK wow, just tried it again and it decided to work? Is version 177 the most up to date, I'd assume not..but would anyone be able to direct me to the version that is?

---

