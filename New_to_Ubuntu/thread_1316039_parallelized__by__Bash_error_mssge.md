---
title: "parallelized  by  Bash error mssge"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by nnjond on 2009-11-05
Hi,

My geek powers have been greatly taxed with trying to achieve my old scrn res after installing 9.10. So I'm following instructions on this Ubuntu pge:  HowTo: NViDIA 185.18 Drivers in Ubuntu 

However my progress has been interrupted by an unexpected error and i don't know how to proceed. Do you understand what it means?

Thanks

It begins ok...


Before doing anything, it's time to say goodbye to nvidia for the moment and bring back the original Xorg configuration. This is done by opening a terminal and running:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
sudo dpkg-reconfigure -phigh xserver-xorg


Next, we need to be ensured that we have all build-essential programs and our current kernel headers.
Code:

sudo apt-get install build-essential pkg-config linux-headers-$(uname -r)

(But then...)

nnjond@den-desktop:~$ sudo apt-get install build-essential pkg-config linux-headers-$(uname -r)
[sudo] password for nnjond: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
pkg-config is already the newest version.
linux-headers-2.6.31-14-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  nvidia-settings
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up nvidia-185-kernel-source (185.18.36-0ubuntu9) ...
Removing old nvidia-185.18.36 DKMS files...

------------------------------
Deleting module version: 185.18.36
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-185.18.36 DKMS files...
First Installation: checking all kernels...
Building for architecture i686
Building initial module for 2.6.31-14-generic

Error! Bad return status for module build on kernel: 2.6.31-14-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia/185.18.36/build/ for more information.
dpkg: error processing nvidia-185-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 nvidia-185-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
nnjond@den-desktop:~$ 


I'm hoping a couple of simple commands will right this.

---

### Post by nnjond on 2009-11-06
This prob dissapeared on a re-install.

---

