---
title: "Trouble with installing nvidia drivers"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by tenfortytwo on 2010-05-15
I've looked at several forums and tried many diffrent things but I just seem to be stuck.  I can stop gdm but even then during the install the install fails.  This is the log file


nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat May 15 01:33:41 2010

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
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
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
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.32-22-generic/build'
-> Kernel output path: '/lib/modules/2.6.32-22-generic/build'
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


I'm paretty new to linux so i'm not sure what exactly is the problem.  something about the kernal not matching?  I have a 8600 gts video card if that helps and I have ubuntu 10.04 LTS

---

### Post by Sealbhach on 2010-05-15
Are you installing from the menu System/Administration/Harware Drivers or did you download from the Nvidia website?

.

---

### Post by tenfortytwo on 2010-05-15
downloaded from nvidia site.  is there a better way to install it?

---

### Post by cascade9 on 2010-05-15
Its a lot easier with ubntu to just go where Sealbhach suggested (System-> Administration-> Harware Drivers) and let ubuntu install the drivers for you than to use the downloaded nvidia installer ;)

---

### Post by tenfortytwo on 2010-05-15
I had tried that originally but then ubuntu stalled out at the startup splash screen and it took me forever to figure out how to get rid of those drivers so i could get back into ubuntu.  Now when I go to system>admin.>hardware drivers it says there are no proprietary drivers in use on this system and there is nothing to click except close and help

---

### Post by tenfortytwo on 2010-05-16
bump

---

### Post by lkraemer on 2010-05-16
Why don't you go to the Nvidia site and just download the latest
drivers for your video card.  Then follow this website for the
install.  I couldn't get mine installed by using the Hardware Drivers...


Reference:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

Version: 195.36.24 Certified
Release Date: 2010.04.28
Operating System: Linux
Language: English (U.S.)
File Size: 32.3 MB
	
GeForce 8 series:
8800 GTS, 8800 GT, 8500 GT, 8300, 8300 GS, 8400 SE, 8800 GTS 512, 8200, 8800 GTX, 8600 GS, 8100 / nForce 720a, 8200 / nForce 730a, 8800 GS, 8600 GT, 8400 GS, 8600 GTS, 8800 Ultra, 8400

GeForce 8M series:
8200M G, 8800M GS, 8800M GTX, 8400M GT, 8700M GT, 8400M GS, 8400M G, 8600M GT


**INSTALL THE DRIVERS:**

**AFTER THE DRIVERS ARE INSTALLED: **
If you are NOT in the GUI (maybe you have a blank screen after boot-up)
Do CTRL+ALT+F1 to get to a tty, and login with your username and password.
Then depending on your desktop environment, run
For Gnome (Ubuntu) = gdm: Kubuntu = kdm XFCE = xdm
```

sudo /etc/init.d/gdm stop

```
Run the reconfiguration
First start by making a manual backup (even though one will be auto-generated
in the form xorg.conf.YearMonthDayTime):
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```
Now run the configuration:
```

sudo dpkg-reconfigure xserver-xorg -phigh

```
Restart the GUI

You are in a tty, so run:
```

sudo /etc/init.d/gdm start

```
Then restart X.
```

startx

```

This fixed mine from being locked in 640x480 mode.

lk

---

