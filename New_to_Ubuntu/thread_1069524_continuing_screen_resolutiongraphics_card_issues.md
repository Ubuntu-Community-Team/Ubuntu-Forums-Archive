---
title: "continuing screen resolution/graphics card issues"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by joemacnz on 2009-02-14
Ever since I "upgraded " to Intrepid, I have not had my screen resolution or grahics card working properly. I have just put up with it for ages, but I can't even play GL-117. I have tried changing the screen resolution through System >> prefs >> screen resolution, but this offers nothing like my screens stated resolution.I have [ this]("http://www.chimei.com.tw/en/product_list.asp?mainclassid=4&subclassid=9&model_no=19") screen. It tells me that we are running 1280 x 1024 @ 0hz.

It should be 1440 x 900 (I think)

I assume this issue stems from the fact that my video card is not set up/not working/not running. Under >>admin >> hardware drivers I am offered "nvidia accelerated graphics driver (version 173 ) recomended"

this now says "driver is activated and currently in use", however, when I restart the computer, I get an error message about "this computer is running in low graphics mode" and and that the graphics card is not going. 

Also, I am not sure why I am not offered Nvidia-177 which is the newest driver.

I realise that there has been a lot written on Ubuntu's screen resolution issues, however, I have trawled through heaps of stuff and tried everything I have seen in print, with no joy.I would really like to sort this issue, once and for all, so any insights would be most appreciated.

JM

---

### Post by RomeReactor on 2009-02-14
Hi. Which video card do you have? People seem to have problems with nVidia cards lower than GeForce FX 5000 series in Intrepid.

---

### Post by joemacnz on 2009-02-14
Yup, that is me. Nvidia GeForce 5700.

---

### Post by RomeReactor on 2009-02-14
According to the [readme]("http://us.download.nvidia.com/XFree86/Linux-x86/180.29/README/appendix-a.html") in the latest (180.29) driver, the [173 driver]("http://www.nvidia.com/object/linux_display_ia32_173.14.12.html") was the last one to support the 5700. Or, seeing as Dapper's support will end in June, you could upgrade to Hardy.

EDIT: Have you tried setting the resolution in the nvidia-settings application?

---

### Post by joemacnz on 2009-02-14
Err, I haven't got dapper, I have Intrepid.

With the Nvidia sttings I get 

> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

---

### Post by joemacnz on 2009-02-14
Under "Hardware Drivers" it now says driver version 173 is "acctivated and in use" , however, with nvidia-settings I still get the error about not having the x driver.

---

### Post by RomeReactor on 2009-02-14
Post the output of:
```
sudo lshw -C display
```

Make sure your software sources don't contain older repositories which might create conflicts. You might also consider uninstalling the current driver, and downloading one from nVidia's site. For Ubuntu 32 bit:
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/NVIDIA-Linux-x86-173.14.12-pkg1.run
```
```
chmod +x NVIDIA-Linux-x86-173.14.12-pkg1.run
```
Then press CTRL+ALT+F1 to go to a text console, login and stop GDM:
```
sudo /etc/init.d/gdm stop
```
Install the driver:
```
sudo ./NVIDIA-Linux-x86-173.14.12-pkg1.run
```
And start GDM again:
```
sudo /etc/init.d/gdm start
```

----------------------------------------------
For Ubuntu 64 bit:
```
wget http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.12/NVIDIA-Linux-x86_64-173.14.12-pkg2.run
```
```
chmod +x NVIDIA-Linux-x86_64-173.14.12-pkg2.run
```
From the console:
```
sudo /etc/init.d/gdm stop
```
Install the driver:
```
sudo ./NVIDIA-Linux-x86_64-173.14.12-pkg2.run
```
And start GDM again:
```
sudo /etc/init.d/gdm start
```

---

### Post by joemacnz on 2009-02-15
sudo lshw -C display returns 

```
 joe@joe-desktop:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: NV36.4 [GeForce FX 5700VE]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga bus_master cap_list
       configuration: driver=nvidia latency=64 maxlatency=1 mingnt=5 module=nvidia



```

I will try the other now and let you know how I get on.

---

### Post by joemacnz on 2009-02-15
Alright, I feel we are getting somewhere now. I followed instructions as instructed ( took a while to work our "pkg1" and not "pkgl")

Anyhow, the installer showed and started but had a few issues, and I ended up aborting at a compiler issue. However, I do have the output from /var/log/nvidia-installer.log, and it goes as follows :

> 

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Feb 16 16:59:14 2009
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
-> Installing NVIDIA driver version 173.14.12.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> The CC version check failed:
   
   The compiler used to compile the kernel (gcc 4.2) does not exactly match the
   current compiler (gcc 4.3).  The Linux 2.6 kernel module loader rejects kern
   el modules built with a version of gcc that does not exactly match that of t
   he compiler used to build the running kernel.
   
   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: Yes)
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).



Does this make sense and is there a way out of this tunnel?

---

### Post by RomeReactor on 2009-02-16
Follow the instructions on posts #2 and #5 [here]("http://www.nvnews.net/vbulletin/showthread.php?t=124315").

---

### Post by joemacnz on 2009-02-16
Okay, I understood to add "CC=gcc-4.2" in front of "./NVIDIA-Linux-x86-173etc", andI checked in Synaptic about kernel headers, and I seem to have a heap there, and I added a few more for luck. I have all the biggest number ones and the *686 ones. I got a little furthur with the install, but now "unable to find the "kernel source tree", in the following log.

```

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Feb 16 21:46:03 2009
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
-> License accepted.
-> Installing NVIDIA driver version 173.14.12.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="gcc-4.2".
-> Performing CC version check with CC="gcc-4.2".
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

:)

---

### Post by RomeReactor on 2009-02-16
Just to make sure:
```
sudo aptitude install linux-headers-`uname -r`
```
Then try the installer again.

Make sure you have **linux-headers-generic** installed.

---

### Post by joemacnz on 2009-02-16
```
Couldn't find any package whose name or description matched "linux-headers-2.6.24-17-386"
Couldn't find any package whose name or description matched "linux-headers-2.6.24-17-386"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


```

---

### Post by joemacnz on 2009-02-16
And the same error message from the installer.

---

### Post by RomeReactor on 2009-02-16
That's odd; Intrepid uses 2.6.27-X. That looks like an old Dapper kernel. Try:
```
sudo aptitude update && sudo aptitude safe-upgrade
```
then try installing the headers again:
```
sudo aptitude install linux-headers-`uname -r`
```

Are you sure you're on Intrepid? If so, try rebooting, go into grub, and see if you get a 2.6.27-X kernel there, and boot into that.

---

### Post by joemacnz on 2009-02-16
```
 joe@joe-desktop:~$ cat /etc/issue
Ubuntu 8.10 \n \l
 
```

I am not sure how to go into grub. This is a dedicated ubuntu box and has been since I built it (and installed Dapper)

however, in /boot/grub, is the following.

```


# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=8a48e06f-755d-423c-b1a4-4bdc2e14cc12 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-17-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-386 root=UUID=8a48e06f-755d-423c-b1a4-4bdc2e14cc12 all_generic_ide
initrd		/boot/initrd.img-2.6.24-17-386

title		Ubuntu 8.04, kernel 2.6.24-17-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-386 root=UUID=8a48e06f-755d-423c-b1a4-4bdc2e14cc12 ro single
initrd		/boot/initrd.img-2.6.24-17-386

title		Ubuntu 8.04, kernel 2.6.24-16-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=8a48e06f-755d-423c-b1a4-4bdc2e14cc12 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-386

title		Ubuntu 8.04, kernel 2.6.24-16-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=8a48e06f-755d-423c-b1a4-4bdc2e14cc12 ro single
initrd		/boot/initrd.img-2.6.24-16-386

title		Ubuntu 8.04, kernel 2.6.22-14-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=8a48e06f-755d-423c-b1a4-4bdc2e14cc12 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 8.04, kernel 2.6.22-14-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=8a48e06f-755d-423c-b1a4-4bdc2e14cc12 ro single
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 8.04, kernel 2.6.20-16-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=8a48e06f-755d-423c-b1a4-4bdc2e14cc12 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu 8.04, kernel 2.6.20-16-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=8a48e06f-755d-423c-b1a4-4bdc2e14cc12 ro single
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu 8.04, kernel 2.6.17-11-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=8a48e06f-755d-423c-b1a4-4bdc2e14cc12 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-386

title		Ubuntu 8.04, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=8a48e06f-755d-423c-b1a4-4bdc2e14cc12 ro single
initrd		/boot/initrd.img-2.6.17-11-386

title		Ubuntu 8.04, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=8a48e06f-755d-423c-b1a4-4bdc2e14cc12 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386

title		Ubuntu 8.04, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=8a48e06f-755d-423c-b1a4-4bdc2e14cc12 ro single
initrd		/boot/initrd.img-2.6.17-10-386

title		Ubuntu 8.04, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=8a48e06f-755d-423c-b1a4-4bdc2e14cc12 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386

title		Ubuntu 8.04, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=8a48e06f-755d-423c-b1a4-4bdc2e14cc12 ro single
initrd		/boot/initrd.img-2.6.15-27-386

title		Ubuntu 8.04, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=8a48e06f-755d-423c-b1a4-4bdc2e14cc12 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386

title		Ubuntu 8.04, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=8a48e06f-755d-423c-b1a4-4bdc2e14cc12 ro single
initrd		/boot/initrd.img-2.6.15-23-386

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST


```

---

### Post by RomeReactor on 2009-02-16
When you turn on the system, after the motherboard manufacturers' screen, you should get a message saying "Press ESC to enter grub", with a timer counting down from 3 to zero seconds.

EDIT: You only have Hardy kernels. In 'System->Administration->Software Sources', make sure all repositories are enabled (though you probably don't need "Source"). Please post your sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by joemacnz on 2009-02-16
```


joe@joe-desktop:~$ cat /etc/apt/sources.list

##Standard Ubuntu Packages

deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb http://nz.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse universe #Added by software-properties
deb http://nz.archive.ubuntu.com/ubuntu/ intrepid universe multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ intrepid universe main multiverse restricted #Added by software-properties

deb http://nz.archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu/ intrepid-security restricted main multiverse universe #Added by software-properties

deb http://nz.archive.ubuntu.com/ubuntu/ intrepid-security universe

deb http://nz.archive.ubuntu.com/ubuntu/ intrepid main restricted

deb http://nz.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse #Added by software-properties


##Wine

# deb http://wine.budgetdedicated.com/apt hardy main
deb-src http://wine.budgetdedicated.com/apt intrepid main



##Cipherfunk multimedia packages (PGP key: 33BAC1B3)

##deb ftp://cipherfunk.org/pub/packages/ubuntu/ edgy main
##deb-src ftp://cipherfunk.org/pub/packages/ubuntu/ edgy main

##Dapper PLF

##deb http://packages.freecontrib.org/ubuntu/plf/ edgy free non-free
##deb-src http://packages.freecontrib.org/ubuntu/plf/ edgy free non-free


#AUTOMATIX REPOS START

deb http://nz.archive.ubuntu.com/ubuntu/ intrepid-security multiverse




deb http://nz.archive.ubuntu.com/ubuntu/ intrepid-updates universe multiverse

#AUTOMATIX REPOS END
deb http://www.debian-multimedia.org/ sid main
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "gutsy gibon"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs


deb http://nz.archive.ubuntu.com/ubuntu/ intrepid-proposed universe main multiverse restricted
deb-src http://nz.archive.ubuntu.com/ubuntu/ intrepid-proposed universe main multiverse restricted #Added by software-properties


deb http://apt.emesene.org/ ./

# deb-src http://apt.emesene.org/ ./


deb http://ppa.launchpad.net/tualatrix/ubuntu hardy main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu intrepid main

deb http://www.debian-multimedia.org etch main

deb-src http://www.debian-multimedia.org etch main

# deb http://download.skype.com/linux/repos/debian stable non-free #Skype
deb http://wine.budgetdedicated.com/apt intrepid main #Wine
deb http://apt.emesene.org/ ./
deb http://blognux.free.fr/ubuntu hardy main
deb-src http://blognux.free.fr/ubuntu hardy main
deb http://download.skype.com/linux/repos/debian/ stable non-free
deb http://snapshots.ekiga.net/snapshots/ubuntu/ intrepid main
joe@joe-desktop:~$ 


```

---

### Post by RomeReactor on 2009-02-16
I suggest you disable the Dapper CD entry, and that you find the correct (Intrepid) version of the blognux.free.fr repository, if there is any.

Also, the tualatrix entries for deb and deb-src don't match.

Other than that, since it appears you only have Hardy kernels, do an update and upgrade, and install the linux-image-generic and linux-headers-generic-packages; that should install at least one of the 2.6.27-X kernels and the headers.
In the future, I think it would help if the ubuntu-desktop package is also installed, in case it's not.

---

### Post by joemacnz on 2009-02-17
Okay, I have done all that, and I am still getting kernel tree issues. I checked my /boot/grub/menu.list and that is still only showing 8.04 kernels, so I downloaded intrepid's installer from here ([http://packages.ubuntu.com/intrepid-updates/i386/kernel-image-2.6.27-11-generic-di/download](http://packages.ubuntu.com/intrepid-updates/i386/kernel-image-2.6.27-11-generic-di/download)) and installed it with ummm, the installer that asked me to. However, my grub menu still doen't have 8.10. No wonder the Nvidia installer can't find it. Where to from here?

---

### Post by RomeReactor on 2009-02-17
You should be able to install one of Intrepid's kernels and corresponding headers through Syanptic or from the terminal:
```
sudo aptitude install linux-image-2.6.27-11-generic linux-headers-2.6.27-11-generic
```
After rebooting, see if grub lists the kernel and if so, boot into it.

EDIT: Note this about the link you posted:
> If you are running Ubuntu, it is strongly suggested to use a package manager like aptitude or synaptic to download and install packages, instead of doing so manually via this website.

You should be able to use any of the listed mirrors by adding a line to your /etc/apt/sources.list like this:

deb [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) intrepid-updates main 

Replacing fr.archive.ubuntu.com/ubuntu with the mirror in question.
debian-installer udeb package

[B]Warning: This package is intended for the use in building debian-installer images only. Do not install it on a normal Ubuntu system.
[/B]

---

### Post by joemacnz on 2009-02-17
Okay, well, I just turned my system into a paper weight I think. I did as instructed, and instlled the bits in the previous post (Linux-image 2.6.27 etc.) Given the option, I went for the new grub menu offered. And that as the last I saw of my system.

I rebooted, and this is what I got.

```


Booting 'Ubuntu 8.10, Kernel Default' root (hd 0,0)

Filesystem type is ext2fs,partition type 0x83

Kernel /boot/vmlinuz root=VVID=8a48e06f-755d-423c-bla4-4bdc2e14cc12 ro quiet splash
[Linux-bzImage,setup0x3000,size=0x221edo]

[o.652084] Kernel panic-not syncing:VFS:Unable to mount root fs on unknown-block(0,0)

(initramfs)


```

And then the keyboard stops responding and the numlock and caps lock light flash.

I also tried the recovery kernel and that outputted a whole lot more before going into kernel panic and offering "initramfs"
All the other kernels offered gave the same result.

After this, I tried using a live CD to get into the system, but after "uncompressing linux" it too reverts to "initramfs"

SO then I disconnected the harddrive and tried the live CD and still I came back to "initramfs", though I can type commands in.
I am writing this from an internet cafe.

Can anyone give a verdict on this? What do I need now? I may be a while responding.

---

### Post by joemacnz on 2009-02-17
Woo hoo, I got back in, but I am not game to turn the computer off now. The issue was with IDE/sata devices at start up,edited grub entry at start up and changed "ro quiet splash" to "all_generic_ide" (not because I am smart, I have had to do it before)

> 

 Originally Posted by bonestonne  View Post
gosh i'd love it if i had bookmarked the page, the solution was posted here somewhere else. lucky for you, i have a habit of writing down millions of notecards with the solutions to this. would printing pages help?

here you go:

when you boot up and you're in Grub, highlight the main Hardy install (with a fresh install its the top one (the other two are a recovery and a memtest).

Press "e" when you highlight the entry on the list.

you'll get to another screen which has a list of 4 entries.
one looks sort of like this:
Code:

Kernel /boot/vmlinuz-2.6.24-16-generic root=BLAHBLAH

(BLAHBLAH is a lot of random stuff, don't worry about what it says exactly)

highlight that line (down arrow to highlight it).

Press "e" again.

you'll now get to a point where you're editing it.

you will see:
Code:

<b-09f2-4836-93ad-e5a70566438d ro quiet splash

now you're in a place where you're editing this. these chages are not permanent at this screen.

at the end, change "ro quiet splash" to "all_generic_ide"

exactly like that, underscores included, but not in quotes.

it should say:
Code:

<b-09f2-4836-93ad-e5a70566438d all_generic_ide

when you're done.

now, press "b". if you hit escape, you'll lose the changes.

you wont see the fancy Ubuntu splash screen, just lots of text. soon it'll get you to the login screen.

now, you need to make the change permanent.

open up terminal (Applications>Accessories>Terminal)

type: "gksu gedit /boot/grub/menu.lst"

this is your grub boot list and menu. you don't want to make a point of playing with this unless you're sure you know what you're doing.

In this file, you will find the same line you just edited:
Code:

<b-09f2-4836-93ad-e5a70566438d ro quiet splash

change that exactly as you did to:
Code:

<b-09f2-4836-93ad-e5a70566438d all_generic_ide

click the save button.

you have fixed your install.

this worked for me, and i wish i was able to find the original poster.

i hope you're able to follow easily, that's exactly how the original instructions had said it.



,now back to my graphics issues...

---

