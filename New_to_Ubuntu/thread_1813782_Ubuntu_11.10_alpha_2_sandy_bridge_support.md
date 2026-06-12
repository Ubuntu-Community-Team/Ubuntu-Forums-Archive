---
title: "Ubuntu 11.10 alpha 2 sandy bridge support"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by razorxpress on 2011-07-28
**[B]Review of Ubuntu 11.10 alpha 2**[/B]

My experience with Ubuntu 11.04 and now with Ubuntu 11.10 is mixed. ATI propitiatory never worked for me. Even not in Ubuntu 11.10. I am writing this for all of you who are looking for decent graphics support in their sandy bridge processor. 

**Problems I had in Ubuntu 11.04**

Though the system was stable, I had fan continuously running until I modified /etc/default/grub with

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=linux pci=noacpi"

Only adding acpi_osi did not work. The problem was I was not able to boot. The computer froze with some black screen.

After being able to run the computer, I found 3D was enabled, but it was very slow. I straight way went to enable the propitiatory driver. Even then 3D effect did not improve. Worst of all it now always went to fall-back mode i.e no 3D support. It had some kind of libGL error. I could not run glxgears. Following [Ubuntu_Natty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide") I removed fglrx and re-installed default and reinstalled intel driver. This time i did not install ati driver.

I was able to play AssultCube, but AlienArena did very bad.

**Transition**
So to have all-round support(sandy bridge) I planned to upgrade Ubuntu 11.04 to Ubuntu 11.10 alpha2. However I looked at some posts and found out I could not install it on USB. So, the solution was to do upgrade from 11.04. It was a hard decision. I knew from past, something would break, even if I had the graphics support. Anyways, it was 1.6GB download(with all the packages I had installed), which took very long time.

**Problems**
I rebooted, and as expected error message was waiting to greet me. It was due to GPU lock. I ignored it. I have to make a habit of living with those buddies if I have to run alpha2. One subtle difference compared to 11.04 is that the Unity is not as bad as it was in 10.04. Lightdm loads very fast. Next was the phase of trying to install the propitiatory ATI driver. Which, again failed. So I had to follow same guide(as above) and reinstall the default graphics packages.

Next to find if Intel had written the graphics drivers well, I planned to run AlienArena. However it did not load. The problem was nothing to do with graphics driver or installation. AlienAreana did not read /usr/share/games but tried to read it from some other place may be /usr/share/. Another place from where it could read was .config/alien-arena of home directory. So I had to first remove .config/alien-arena directory(which it linked any way, due to permission issue i had to use sudo). 

$sudo rm -rf ~/.config/alien-arena. 
$mkdir ~/.config/alien-arena
$cd ~/.config/alien-arena
$ln -s /usr/share/games/alien-arena/botinfo/
$ln -s /usr/share/games/alien-arena/data1/

Then it worked like charm. The best part is that, now I can run it in full screen 1360x768 mode, with best settings, vsync enabled.

I have some problems like if I try to install from software center it loads fan with full throttle. So i will be using command line for time being. I know I will have many problems with this alpha release, which I will list out as I find them, besides some hick ups. I can live with them. If I completely break this alpha 2 with major changes, I still have windows 7 as a reboot. Since, I boot grub boot loader from windows boot loader, I am always safe.

---

