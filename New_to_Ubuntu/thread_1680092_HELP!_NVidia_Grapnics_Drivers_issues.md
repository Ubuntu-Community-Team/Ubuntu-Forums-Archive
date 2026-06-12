---
title: "HELP! NVidia Grapnics Drivers issues"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by Musicjunkie4537 on 2011-02-02
So I followed the steps in the Nvidia Latest Drivers article [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

Now my computer can only boot to low graphics mode.  How do I fix this or get more information about the bug?

My card is an NVidia Galaxy GeForce 8400GS

any tips?

---

### Post by taseedorf on 2011-02-02
Make SURE you're identifying the card right.

Download the right driver.

in terminal, go to the directory you have it and do sudo chmod +x ./NV*
 then exit gdm by

sudo /etc/init.d/gdm stop

then once you get a command line

go to the directory of the driver and type

sudo ./NV*

should work!


FYI, once you shutdown gdm it MAY be needed to switch to a different tty ctrl + alt + 6 for example

---

### Post by Musicjunkie4537 on 2011-02-02
It said there was some kind of an error installing the drivers.  It told me to look at the NVidia Installer log.

Originally I installed the NVidia drivers using Additional drivers to get the proprietary driver, but it didn't seem to work properly on my current OS

It seems that the distribution provided pre-install scripts failed, so I decided to just cancel out of the installation right then and there to avoid making the problem bigger

Here's the log:

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Feb  2 12:35:39 2011
installer version: 256.53

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
-> Installing NVIDIA driver version 256.53.
-> There appears to already be a driver installed on your system (version: 256.
   53).  As part of installing this driver (version: 256.53), the existing driv
   er will be uninstalled.  Are you sure you want to continue? ('no' will abort
   installation) (Answer: Yes)
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation 
   anyway? (Answer: No)
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com]("http://www.nvidia.com").
```

---

### Post by Musicjunkie4537 on 2011-02-02
So I went to the NVidia website just to make sure that i was using the right driver, downloaded it, and ran it in terminal, but I still have the problem

Is there a log file where I can find out more about the installation failure? other than the nvidiainstall.log

---

### Post by steveneddy on 2011-02-02
Are the Nvidia drivers available from the Ubuntu repos not working for you - it would seem a lot easier just to install video drivers that update themselves when the kernel updates.

If you were to go to 

System --> Admiinistration --> Hardware Drivers

The system will offer you the choice of some great Nvidia drivers.

Unless you really need lots of graphical processing - and you are recoeding sound, right? - then the video drivers offered in the repos should do just fine IMHO.

---

### Post by Musicjunkie4537 on 2011-02-02
Yeah, I'll probably just do that.  Right now I'm still getting my stuff set up.  I wanted to get some open source drivers so they don't have the proprietary limitation junk, But for now these ones should be fine

But thanks for the help guys :)

---

### Post by steveneddy on 2011-02-02
> **Musicjunkie4537 said:**
> Yeah, I'll probably just do that.  Right now I'm still getting my stuff set up.  I wanted to get some open source drivers so they don't have the proprietary limitation junk, But for now these ones should be fine

But thanks for the help guys :)

I hope this works for you - I recently tried to get a good recording rig set up with Ubuntu Studio but grew increasingly frustrated with Jack.

---

