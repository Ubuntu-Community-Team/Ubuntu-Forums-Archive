---
title: "Update driver via command line"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by bushtech on 2010-09-25
Hi all
I'm trying to update my graphics driver via command line. computer stuck - can only access terminal.

The example I got off a forum:
**root@dcerouter:~#** wget [http://us.download.nvidia.com/XFree86/Linux-x86/](http://us.download.nvidia.com/XFree86/Linux-x86/)*<version>*/NVIDIA-Linux-x86-*<version>*-pkg1.run

I've tried: 
root@kkserver:~# wget [http://us.download.nvidia.com/XFree86/Linux-x86/256.53/NVIDIA-Linux-x86-256.53](http://us.download.nvidia.com/XFree86/Linux-x86/256.53/NVIDIA-Linux-x86-256.53)[COLOR=Orange]-pkg1.run
[/COLOR]
and:
root@kkserver:~# wget [http://us.download.nvidia.com/XFree86/Linux-x86/256.53/NVIDIA-Linux-x86-256.53](http://us.download.nvidia.com/XFree86/Linux-x86/256.53/NVIDIA-Linux-x86-256.53).[COLOR=Orange]run-pkg1.run[/COLOR]

Both connect OK but come back with &quot; ERROR 404: not found

Am I doing something stupid? Please help a linux noobie
TIA

---

### Post by andrewthomas on 2010-09-29
What is wrong with nvidia-current?

```
aptitude show nvidia-current
Package: nvidia-current                  
New: yes
State: not installed
Version: 256.53-0ubuntu3
Priority: optional
Section: restricted/misc
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 129M
Depends: x11-common (>= 1:7.0.0), make, sed (> 3.0), dkms, linux-libc-dev, libc6-dev, linux-headers-generic | linux-headers,
         patch, acpid, libc6 (>= 2.2.5), libgcc1 (>= 1:4.1.1), libx11-6, libxext6, libxv1, libxvmc1, zlib1g (>= 1:1.1.4)
Recommends: nvidia-settings
Provides: xorg-driver-video, xserver-xorg-video-8
Description: NVIDIA binary Xorg driver, kernel module and VDPAU library
 The binary driver provide optimized hardware acceleration of OpenGL applications via a direct-rendering X Server. AGP, PCIe,
 SLI, TV-out and flat panel displays are also supported. 
 
 This package also includes the source for building the kernel module required by the Xorg driver, and provides NVIDIA's
 implementation of the Video Decode and presentation API. The latter enables acceleration for NVIDIA 8 and later series cards
 for h264 video. 
 
 GPUs such as GeForce series 6 or newer are supported. 
 
 See **/usr/share/doc/nvidia-current/README.txt.gz for a complete list of supported GPUs and PCIIDs**

```

---

