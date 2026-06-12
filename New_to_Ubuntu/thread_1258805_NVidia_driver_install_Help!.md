---
title: "NVidia driver install: Help!"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by rob86 on 2009-09-05
I'm having trouble installing an nVidia 5200 video card driver. I solved a few problems myself by googling, but now I'm stuck (why is this stuff so difficult!)

It says a bunch of stuff, and then fails. I could repeat it, but it's much more clear in the log file so I'll just paste it:

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 173.14.20.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
ERROR: Unable to connect to remote host download.nvidia.com (Connection
       refused)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.
ERROR: Installation has failed.


Any idea what all this means?

---

### Post by wojox on 2009-09-05
To make it real easy go to System > Admin > Synaptic

Search nvidia and mark your 173.XX for installation.

---

### Post by chriskin on 2009-09-05
or install the envyng (with a gui if you want) from synaptic and have it take care of the installation of the drivers

---

