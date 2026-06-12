---
title: "Cannot install nVidia drivers for ethernet"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by eljoubert on 2007-04-24
I have dug around and haven't yet found a post with my specific problem. So, here goes...

I just purchased a new motherboard (MSI K9N6GM series) with onboard LAN and audio. After installing Edgy, I noticed had no network connectivity. Running sudo lshw -C network showed nothing. So, I downloaded the nVidia drivers (NFORCE-Linux-x86-1.0-0310-pkg1.run) and tried to install them, but was notified that my computer did not have the necessary libc header files. I found this to be quite odd considering that my Synaptic Package Manager shows the following as already being installed:

linux-headers-2.6.17-10
linux-headers-2.6.17-10-generic
linux-headers-generic

What am I doing wrong?

NOTE: If you are wondering, I am using a USB memory stick to move the files to the computer.

---

### Post by hardyn on 2007-04-24
Its looking for the standard C library files, not the kernel headers, I think you may have to install libc6 maybe GCC?, but i kinda thought that should have been installed by default?

what is the exact error message?  while cryptic, they are usually pretty informative.

---

### Post by eljoubert on 2007-04-26
Thanks for thge reply...I tried to install Libc6, but a newer version already existed. Anyways. The exact message I get while trying to install the nVidia drivers is:

[COLOR="Blue"]No precompiled kernel interface was found to match your kernel; this means that the installer will need to compile a new kernel interface.[/COLOR]

followed by

[COLOR="Blue"]ERROR: You do not appear to have libc header files installed on your system. 
         Please install your distribution's libc development package.[/COLOR]

followed by

[COLOR="Blue"]ERROR: Installation of the network driver has failed.  Please see the file   
         '/var/log/nvidia-nforce-installer.log' for details.  You may find     
         suggestions on  fixing installation problems in the README available  
         on the Linux driver download page at [www.nvidia.com](www.nvidia.com).[/COLOR]

---

### Post by Barrakketh on 2007-04-26
Install the build-essential package and try building the drivers after that.

---

### Post by eljoubert on 2007-05-02
I tried installing build-essential, but was missing some packages. I managed to get all the packages needed, but ran into a problem with installing 2 of them (g++-4.1 & libstdc++6-4.1-dev). They both indicate the other needs to exist first.

---

