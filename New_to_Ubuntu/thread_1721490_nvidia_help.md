---
title: "nvidia help"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by onus on 2011-04-04
please give your gracious direction in this my moment of tribulation.

not the best with computers need some input. 
thnx!

i have an Asus M4A78LT-M motherboard 
NVIDIA GeForce 8600 GT graphix card
Ubuntu 10.10 
Linux Kernel 2.6.32-27

and no internet access for this tower... 

i had access at school w/ this tower where i installed the 173 version driver but it did not work... so i was forced to remove and i would like to install the newer release w/o having to haul this computer all the way back to town... 

NVIDIA made it sound simple enough... 
drop to shell w/o starting X and install by cd to dir and runing file: "sh ./NVIDIA-Linux-x86_64-260.19.44.run"

but it complains about being in run lvl 1 saying it could cause problems (but since i have no Internet what choice do i have?)

mentions something about compiling kernel?

included is the error log 
all help is greatly appreciated.

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Apr  4 15:05:22 2011
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> You appear to be running in runlevel 1; this may cause problems.  For exampl
   e: some distributions that use devfs do not run the devfs daemon in runlevel
   1, making it difficult for `nvidia-installer` to correctly setup the kernel 
   module configuration files.  It is recommended that you quit installation no
   w and switch to runlevel 3 (`telinit 3`) before installing.
   
   Quit installation now? (select 'No' to continue installation) (Answer: No)
-> License accepted.
-> Installing NVIDIA driver version 173.14.12.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.32-27-generic/build'
-> Kernel output path: '/lib/modules/2.6.32-27-generic/build'
ERROR: If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.
       
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the equivalent nvidia-installer command line option.
       
       Depending on where and how the kernel sources (or the
       kernel headers) were installed, you may need to specify
       their location with the SYSSRC environment variable or
       the equivalent nvidia-installer command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by rosencrantz on 2011-04-04
Hi onus,
a) you should be able to use runlevel 3 even without an external network connection.  E.g., quite a lot of internal stuff also uses network adresses (localhost etc.). However, I don't think this is why the install fails.
b) this might be a lot of bother with part of your network connection  being you running to school and back sorting out dependencies, but did you install the kernel headers (package linux-headers)?
c) there seem to be Debian packages up to version 185 (aptitude search nvidia) - I don't know which version your chip requires. Have you tried those? 

Cheers,
rosencrantz

---

