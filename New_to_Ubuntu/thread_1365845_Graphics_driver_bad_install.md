---
title: "Graphics driver bad install?"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by nnjond on 2009-12-27
Hi, Groan! after weeks of low res hell I think i've tracked down the prob to a 2 possibilities : 

# my Nvidia graphics card is so old, it's not compatable with 9.10

or the fault is revealed somewhere in this blizzard of jargon that occured when i attempted a fresh install.

# Error! Bad return status for module build on kernel: 2.6.31-16-generic (i686)

Consult the make.log in the build directory

/var/lib/dkms/nvidia/185.18.36/build/ for more information.

dpkg: error processing nvidia-185-kernel-source (--configure):

 subprocess installed post-installation script returned error exit status 10

Setting up nvidia-185-libvdpau (185.18.36-0ubuntu9) ...



dpkg: dependency problems prevent configuration of nvidia-glx-185:

 nvidia-glx-185 depends on nvidia-185-kernel-source (>= 185.18.36); however:

  Package nvidia-185-kernel-source is not configured yet.

dpkg: error processing nvidia-glx-185 (--configure):

 dependency problems - leaving unconfigured

Setting up nvidia-settings (180.25-0ubuntu1) ...

No apport report written because the error message indicates its a followup error from a previous failure.


Processing triggers for libc-bin ...

ldconfig deferred processing now taking place

Errors were encountered while processing:

 nvidia-185-kernel-source

 nvidia-glx-185

---

### Post by ankspo71 on 2009-12-28
Hi,
If nvdia drivers 185 and 173 don't work because your nvidia graphics card is outdated, there is still one more driver possibility. That is to try the oldest nvidia driver currently available in Ubuntu 9.10. If you are interested, go into 'synaptic package manager' and search for nvidia, then look for all of the entries that have the 96 version number. There should be four of them. Install all of them nvidia 96 packages, It might prompt you that it will remove the 185 drivers. Reboot. Now go to System > Administration > Hardware Drivers, and see if the Nvidia 96 driver is listed in there (it should be). Enable it, then reboot again.

I did this procedure on my wife's computer when I wanted to see if Ubuntu 9.04 worked on her computer. It turns out that 185 and 173 wouldn't work for her (they gave me the black screen), but the 96 version worked out great. She has a 6100 or 6200 GeForce built in graphics card. 
Hope this helps.

---

### Post by nnjond on 2009-12-29
Thanks for your interest. Hardware Drivers found 96 but a problem occurred.


"Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log"


/var/log/jockey.log  includes these ERRORS:


2009-12-29 12:48:18,174 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2009-12-29 12:48:18,175 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2009-12-29 12:48:18,214 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia



2009-12-29 12:48:18,222 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl


2009-12-29 12:48:18,960 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx


2009-12-29 12:48:18,977 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci


2009-12-29 12:48:19,709 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia


2009-12-29 12:48:45,975 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2009-12-29 12:48:45,976 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting


2009-12-29 12:55:35,629 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2009-12-29 12:55:35,629 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting

---

### Post by alzie on 2009-12-29
I was having resolution problems as well.  Between my old computer (athlon 1.8 GHz?) my nVidia geForce 6200 and Ubuntu I wasn't able to get near native resolution.  I ended up using the method described by ST3ALTHPSYCH0 here: [http://ubuntuforums.org/showthread.php?t=1320785](http://ubuntuforums.org/showthread.php?t=1320785) and was able to get from 800x600 to my native resolution of 1280x1024 with nVidia driver 185.18.36

I hope this helps.

---

### Post by nnjond on 2009-12-30
Thanks Alzie. I'm studying the solution. How ever if The problem will go away for the mid-term, I'd just as soon buy an updated graphics card. Do you supose that will solve the problem?

---

