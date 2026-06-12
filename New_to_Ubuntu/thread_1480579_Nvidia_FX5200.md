---
title: "Nvidia FX5200"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by GaaraOfDSand on 2010-05-11
I don't know if this is the right place to put this topic if not please someone put it in the right place where it belongs. Thanks. :)

I just updated xubuntu 10.04 with the latest updates, and the drivers for the graphics card (Nvidia FX5200) have gone mad.. This did happen before but I was always able to reinstall the 173.14.25 through the console login, however this time I can't and I don't know why, I can't adjust the resolution, nvidia-settings is telling me to run nvidia-xconfig and restart the X Server, however when I do, nothing happens, at least no improvements are shown (I believe that only reconfigures the xorg file.) When I try to install the 173.14.25 drivers, it gives me some errors, below is the log /var/log/nvidia-installer.log:

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed May 12 00:40:46 2010
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
  no X server check       : true
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
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '1110'
   of a runnning X server.
-> Continuing per the '--no-x-check' option.
-> The file '/tmp/.X1-lock' exists and appears to contain the process ID '5162'
   of a runnning X server.
-> Continuing per the '--no-x-check' option.
-> License accepted.
-> Installing NVIDIA driver version 173.14.25.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation 
   anyway? (Answer: Yes)
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

Here's what the 173.14.25 is giving me:

```
The distribution-provided pre-install script failed!  Continue installation
  anyway?
```

And I click Yes

```
ERROR: Unable to find the kernel source tree for the currently running       
         kernel.  Please make sure you have installed the kernel source files  
         for your kernel and that they are properly configured; on Red Hat     
         Linux systems, for example, be sure you have the 'kernel-source' or   
         'kernel-devel' RPM installed.  If you know the correct kernel source  
         files are installed, you may specify the kernel source path with the  
         '--kernel-source-path' command line option.

```

I click OK

```
  ERROR: Installation has failed.  Please see the file
         '/var/log/nvidia-installer.log' for details.  You may find            
         suggestions on fixing installation problems in the README available   
         on the Linux driver download page at www.nvidia.com.
```

I would be happy to provide any additional information needed.

Thanks in advance for the help.

And excuse me for the very long post

---

### Post by slicq on 2010-05-21
**Try this: **[http://ubuntuforums.org/showthread.php?t=1467074](http://ubuntuforums.org/showthread.php?t=1467074)

---

### Post by geerm on 2010-05-21
installing with  -k $(uname -r) -f helped me "install it" how ever i still got the same errors when trying to use them

---

### Post by geerm on 2010-05-21
Hmm. , was following [http://ubuntuforums.org/showpost.php?p=9211609&postcount=35](http://ubuntuforums.org/showpost.php?p=9211609&postcount=35) and just after  

sudo apt-get --purge remove xserver-xorg-video-nouveau

i restarted and the drivers are now working ( i had installed them previously with the -k $(uname -r) -f )

so i'm guessing it was that xserver that was giving me trouble.

---

### Post by GaaraOfDSand on 2010-05-27
Thank you all for the replies and sorry I couldn't get back to you all earlier I was kinda busy..

I tried with the -k $(uname -r) -f command, it started downloading the latest drivers which are 19* not 17*, so they're not compatible with my gfx card. :\

Anything else I should try?

@slicq I followed that post you gave me, with no results.. Right now I'm on low-graphics mode.

Hope to hear from you guys and thanks!

EDIT: Ok I think the Nvidia FX5200 card is not supported by the Kernel 2.6.32-22-generic, each time I install it, my graphics are messed up. 

So here's what I did:

Use mousepad or gedit whatever you like and edit the file /boot/grub/grub.cfg

Look for this line: ### BEGIN /etc/grub.d/10_linux ### and delete everything in between 

### BEGIN /etc/grub.d/10_linux ### 

And

menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 4fc5b550-81e6-4c08-bfd2-c5b1602a92dd
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=4fc5b550-81e6-4c08-bfd2-c5b1602a92dd ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 4fc5b550-81e6-4c08-bfd2-c5b1602a92dd
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=4fc5b550-81e6-4c08-bfd2-c5b1602a92dd ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}

So it'll look something like this:

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 4fc5b550-81e6-4c08-bfd2-c5b1602a92dd
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=4fc5b550-81e6-4c08-bfd2-c5b1602a92dd ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 4fc5b550-81e6-4c08-bfd2-c5b1602a92dd
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=4fc5b550-81e6-4c08-bfd2-c5b1602a92dd ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

I know the kernel is not updated this way but at least the graphics work and we can still use the FX5200 :D

---

### Post by lewistech on 2010-07-14
> **geerm said:**
> Hmm. , was following [http://ubuntuforums.org/showpost.php?p=9211609&postcount=35](http://ubuntuforums.org/showpost.php?p=9211609&postcount=35) and just after  

sudo apt-get --purge remove xserver-xorg-video-nouveau

i restarted and the drivers are now working ( i had installed them previously with the -k $(uname -r) -f )

so i'm guessing it was that xserver that was giving me trouble.



Worked for me... Thanks!

---

