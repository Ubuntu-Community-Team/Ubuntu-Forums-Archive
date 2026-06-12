---
title: "Washed out videos"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by nnjond on 2010-08-08
Hi,

I'm one of many people who have failed to install the recommended driver Nvidia-173. In my latest install of Lucid, the video colours are all washed out and i don't seem to have any possible adjustments. Can you advise me please ?

Thanks for your time.

---

### Post by gordintoronto on 2010-08-08
What do you see under Administration/Hardware Drivers?

---

### Post by nnjond on 2010-08-08
Thanks for your interest

Nvidia 173 is recommended (but intall has failed many times)

Also Nvidia 96 , If i tried that, it was long ago, and failed.

---

### Post by davidmohammed on 2010-08-08
are you using the standard kernel that came with lucid or have you install a newer kernel?

Reason I ask - if you have a newer kernel you need to ensure that the linux headers with that kernel are also installed so that the nvidia drivers have something to compile against.

---

### Post by nnjond on 2010-08-08
If i was prompted to install an update, i did. But this problem with 173 has existed since 9.10

---

### Post by davidmohammed on 2010-08-08
looks very much that you've got clashing drivers - probably due to you having upgraded from karmic when you installed the drivers from the nvidia website -- sounds correct?

what have you tried to do to install the nvidia drivers?

something like [this]("http://www.sucka.net/2010/04/how-to-install-nvidia-video-driver-in-10-04-lucid-lynx/") blog?

---

### Post by nnjond on 2010-08-08
This , like others, is a fresh install. Hardware Drivers claims:

No proprietary drivers are in use on this system

Will study your advice

---

### Post by nnjond on 2010-08-09
Once again attempt to install the recommended 173 driver following your advice has failed. (See below). I Suppose i need an alternative driver to normalise the appearance of my videos.

```
nnjond@linx-desktop:~$ sudo apt-get install nvidia-current
[sudo] password for nnjond: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  nvidia-settings
The following NEW packages will be installed
  nvidia-current nvidia-settings
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 24.1MB of archives.
After this operation, 74.5MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  nvidia-settings
Install these packages without verification [y/N]? y
Get: 1 http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/restricted nvidia-current 195.36.24-0ubuntu1~10.04 [23.3MB]
Get: 2 http://gb.archive.ubuntu.com/ubuntu/ lucid/main nvidia-settings 195.36.08-0ubuntu2 [819kB]              
Fetched 24.1MB in 10s (2,303kB/s)                                                                              
Selecting previously deselected package nvidia-current.
(Reading database ... 175497 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_195.36.24-0ubuntu1~10.04_i386.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_195.36.08-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up nvidia-current (195.36.24-0ubuntu1~10.04) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group gl_conf) doesn't exist.
update-initramfs: deferring update (trigger activated)
Loading new nvidia-current-195.36.24 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-24-generic
Building for architecture i686
Building initial module for 2.6.32-24-generic

Error! Bad return status for module build on kernel: 2.6.32-24-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-current/195.36.24/build/ for more information.
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up nvidia-settings (195.36.08-0ubuntu2) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
Processing triggers for python-support ...
Errors were encountered while processing:
 nvidia-current
E: Sub-process /usr/bin/dpkg returned an error code (1)
nnjond@linx-desktop:~$ sudo modprobe nvidia-current
FATAL: Module nvidia_current not found.
nnjond@linx-desktop:~$ 

```

---

### Post by davidmohammed on 2010-08-09
hi there,
 please post the contents of the build.log file mentioned in the post you have made (I think its in the folder /var/lib/dkms/nvidia-current/195.36.24/build/   mentioned in your post)

---

### Post by NewDisciple on 2010-08-09
You don't say which nvidia card you have.  If it is GE Force 6 and above you may want to consider the 256.35 display drivers.
Here is a tutorial that I used that I either got in this forum or the Ultimate Edition forum.

nVidia 256.53 graphics drivers highlights:
Added unofficial GLX protocol support
Improved Thermal Settings reporting in nvidia-settings to accurately reflect hardware configurations with multiple thermal sensors.
Fixed an interaction problem between Compiz and 'screen-scraping' VNC servers like x11vnc and vino that caused the screen to stop updating. 
Enhanced VDPAU to add basic support for Xinerama. VDPAU will now operate on a single physical X screen under Xinerama. See the README for more details.
Enhanced VDPAU's handling of corrupt clips of all formats on GPUs with VDPAU feature set C to be at least as good as on GPUs with VDPAU feature set B. This significantly improves various clips provided by nvnews.net user eamiller.
Fixed a bug in Xv attribute handling that caused hue, saturation,brightness, and contrast values to be misapplied when using an Xv overlay adaptor.
Implemented new APIs to allow sharing VDPAU surfaces with OpenGL andCUDA.
Removed precompiled kernel interfaces from the NVIDIA Linux-x86 .run file;

Important note before trying to upgrade: these drivers will only work with GeForce 6 and above!

The easiest way to upgrade to the latest nVidia 256.35 display drivers in Ubuntu (Maverick, Lucid, Karmic, Jaunty, Intrepid or Hardy) is to use the following PPA (just copy/paste the commands in a terminal):


1. Add the PPA

-For Ubuntu Lucid and Maverick:
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates


-For Ubuntu Karmic, Jaunty, Intrepid and Hardy:
sudo sh -c "echo 'deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) UBUNTU_VERSION main' >> /etc/apt/sources.list"
sudo sh -c "echo 'deb-src [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) UBUNTU_VERSION main' >> /etc/apt/sources.list"
Replace the "UBUNTU_VERSION" in the commands above with your Ubuntu version (karmic, jaunty, intrepid or hardy).

2. Install the nVidia display drivers

-For Ubuntu Lucid and Maverick:
sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings

Then go to System > Administration > Hardware Drivers and make sure "Nvidia current" is activated.


-For Ubuntu Karmic, Jaunty, Intrepid and Hardy:
sudo apt-get update && sudo apt-get install nvidia-glx-256 nvidia-256-modaliases nvidia-settings

Then go to System > Administration > Hardware Drivers and make sure Nvidia 256.35 graphics drivers are activated.


And finally, restart.

If for some reason the new drivers do not work properly, use PPA Purge to remove the PPA and revert all the changes.


Good luck!

---

### Post by davidmohammed on 2010-08-09
some good advice there - newdisciple

just be aware - your trace reports a build error.  Therefore, until that is resolved, you probably will not be able to use any newer nvidia driver.

---

### Post by nnjond on 2010-08-09
Thanks for your interest. Please note the address of content:


nnjond@linx-desktop:/var/lib$ cd /dkms/nvidia-current/195.36.24/build
bash: cd: /dkms/nvidia-current/195.36.24/build: No such file or directory
nnjond@linx-desktop:/var/lib$ cd /var/lib/dkms/nvidia-current/195.36.24/build
nnjond@linx-desktop:/var/lib/dkms/nvidia-current/195.36.24/build$ pwd
/var/lib/dkms/nvidia-current/195.36.24/build
nnjond@linx-desktop:/var/lib/dkms/nvidia-current/195.36.24/build$ ls
conftest.h           make.log       nv-kernel.o  nv-vm.h         os-registry.c
conftest.sh          nvacpi.c       nv-linux.h   nv-vm.o         os-registry.o
cpuopsys.h           nvacpitypes.h  nv-memdbg.h  nv-xen.h        patches
dkms.conf            nv.c           nv-misc.h    os-agp.c        patches.h
gcc-version-check.c  nv_compiler.h  nv.o         os-agp.h        README
makefile             nv_gvi.c       nvreadme.h   os-agp.o        rmil.h
Makefile             nv_gvi.o       nv-reg.h     os-interface.c  rmretval.h
Makefile.kbuild      nv.h           nvtypes.h    os-interface.h  xapi-sdk.h
Makefile.nvidia      nv-i2c.c       nv-vm.c      os-interface.o
nnjond@linx-desktop:/var/lib/dkms/nvidia-current/195.36.24/build$

---

### Post by davidmohammed on 2010-08-09
that's fine - just need the content of the build.log file in that directory

type

gedit make.log

when you are in that directory

---

### Post by nnjond on 2010-08-09
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

---

### Post by davidmohammed on 2010-08-09
thats very confusing ...

ok - can you type

gedit /var/lib/dkms/nvidia-current/kernel-2.6.32-24-generic-i686/log/make.log

and post the output within code tags in your reply.

---

