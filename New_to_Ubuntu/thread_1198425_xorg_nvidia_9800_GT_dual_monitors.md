---
title: "xorg nvidia 9800 GT dual monitors"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by miesnerd on 2009-06-27
Hi-
I'm at the point of desperation.
I currently have an nvidia 9800 GT graphics card that I used to be able to get to work with both of my monitors. I cant get that anymore (screwed up when a new kernel was installed). Anyways, I'm at the point where I'm willing to actually buy new monitors to get this to work. I currently have a 1440x 900 X2gen (which I cant get to work at the same time as the primary monitor) and a  Viewsonic 19" 1280X1024 monitor.

Miesnerd

---

### Post by northern lights on 2009-06-27
While I'd personally never buy a, if not two monitor(s), even if they were the cause of this (temporary) problem, let me venture to guess that they aren't anyhow. The issue most likely lies with the currently loaded nvidia driver's kernel module version. And is on top of that probably solvable via options - i.e. I doubt you'd even have to alter drivers to get it to work again. It's likely that either previous configurations have been overwritten, or that changes have been made to the driver such that new settings are required.

Can you post the output of```
aptitude search nvidia
```

Have you tried booting any the previous kernels (GRUB menu - automatically displayed if dual booting any other OS and/or distro, invoked via hitting 'ESC' key at boot if Ubuntu is the sole OS on the machine)?

Are one (X Screen 0) or two (X Screens 0 & 1) monitors available under 'System > Administration > NVIDIA X Server Settings'?

In the same app, what happens if you hit 'Detect Displays' under 'X Server Display Configuration'?

---

### Post by miesnerd on 2009-06-27
```
p   nvidia-173-kernel-source        - NVIDIA binary kernel module source        
i   nvidia-173-modaliases           - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-180-kernel-source        - NVIDIA binary kernel module source        
p   nvidia-180-libvdpau             - Video Decode and Presentation API for Unix
p   nvidia-180-libvdpau-dev         - Video Decode and Presentation API for Unix
i   nvidia-180-modaliases           - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-71-kernel-source         - NVIDIA binary kernel module source        
i   nvidia-71-modaliases            - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-96-kernel-source         - NVIDIA binary kernel module source        
i   nvidia-96-modaliases            - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-cg-toolkit               - NVIDIA Cg Toolkit Installer               
i   nvidia-common                   - Find obsolete NVIDIA drivers              
v   nvidia-glx                      -                                           
p   nvidia-glx-173                  - NVIDIA binary Xorg driver                 
p   nvidia-glx-173-dev              - NVIDIA binary Xorg driver development file
p   nvidia-glx-180                  - NVIDIA binary Xorg driver                 
p   nvidia-glx-180-dev              - NVIDIA binary Xorg driver development file
p   nvidia-glx-71                   - NVIDIA binary Xorg driver                 
p   nvidia-glx-71-dev               - NVIDIA binary Xorg driver development file
p   nvidia-glx-96                   - NVIDIA binary Xorg driver                 
p   nvidia-glx-96-dev               - NVIDIA binary Xorg driver development file
v   nvidia-glx-dev                  -                                           
p   nvidia-kernel-common            - NVIDIA binary kernel module common files  
v   nvidia-kernel-source            -                                           
p   nvidia-settings                 - Tool of configuring the NVIDIA graphics dr

```
There's the output, but here's the thing. In anticipation of making some sort of move towards dual screens, I have once again backed up and done a fresh install.
In the past, though, I can tell you that what has happened has been that I've tried to boot into the most recent kernel (when I realized that the newest installed one f'd my config) and as I booted into it, ya know what, the nvidia drivers did the same "install" type of thing to the kernel to f up that kernel as well.

---

### Post by miesnerd on 2009-06-27
using any tool except for nvidia-settings to detect my 1440X900 display while the primary display is running proves futile. nvidia-settings is, when installed, the only one that can detect it, but I cannot ever configure it to work properly.

Every other tool acts as if it doesnt exist.
Keep in mind that right now, nvidia-settings is not installed as I have just done a clean install.

---

### Post by northern lights on 2009-06-27
The most [recent nvidia Linux driver supports your card]("http://us.download.nvidia.com/XFree86/Linux-x86/185.18.14/README/appendix-a.html"). If previous versions you ran did, the one [currently in the jaunty repos]("http://packages.ubuntu.com/search?suite=jaunty&section=all&arch=any&searchon=names&keywords=nvidia-glx-180") thus also should.

Install the driver```
sudo apt-get update && sudo apt-get install nvidia-glx-180
``` and check 'System > Administration > NVIDIA X Server Settings' again.

[EDIT]
*nvidia-settings* will automatically be installed with the 180.X display driver
[/EDIT]

---

### Post by miesnerd on 2009-06-27
ok I'm doing it now, but I have to warn you: I've done this and used their gui to try to get the dual monitors configured probably a dozen or so times, with no luck.

---

### Post by miesnerd on 2009-06-27
ok im back, and as expected, yes, undder X server display info, both screens are available, but it labels as CRT (which is a 140x900 LCD) is disabled.

Just as a note, I only have X screen 0, there's no other x screen.

---

