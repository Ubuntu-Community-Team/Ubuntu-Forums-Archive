---
title: "Driver selection"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by jsvannorman on 2010-12-23
Please be kind, I'm an absolute newbie to Ubuntu and Linux (although really like it thus far), so I'm still learning the basics. 
 
I just installed Ubuntu on a HTPC I'm building and need to install some of the drivers. Right now I'm working on the driver for the motherboard Realtek HD audio. The software CD that came with the motherboard has three different Linux drivers, one for Fedora (realtek-linux-audiopack-4.06x.tar.bz2), one for RedHat (realtek-linux-audiopack-RHEL4U4-HDA-4.05g.tar.bz2), and one for SUSE (realtek-linux-audiopack-4.06x.tar.bz2  - again). I also went to the Realtek website and found another general Linux driver (LinuxPkg_5.15rc21.tar.bz2). 
 
So my question is, which one works with Ubuntu? If this has been covered in a previous thread, my apologies - just point me in the right direction. Thanks!
 
John

---

### Post by gandaran on 2010-12-23
> **jsvannorman said:**
> Please be kind, I'm an absolute newbie to Ubuntu and Linux (although really like it thus far), so I'm still learning the basics. 
 
I just installed Ubuntu on a HTPC I'm building and need to install some of the drivers. Right now I'm working on the driver for the motherboard Realtek HD audio. The software CD that came with the motherboard has three different Linux drivers, one for Fedora (realtek-linux-audiopack-4.06x.tar.bz2), one for RedHat (realtek-linux-audiopack-RHEL4U4-HDA-4.05g.tar.bz2), and one for SUSE (realtek-linux-audiopack-4.06x.tar.bz2  - again). I also went to the Realtek website and found another general Linux driver (LinuxPkg_5.15rc21.tar.bz2). 
 
So my question is, which one works with Ubuntu? If this has been covered in a previous thread, my apologies - just point me in the right direction. Thanks!
 
John
you don't need to install any drivers, the default open source drivers should work fine but if you are not happy with them then you can install the proprietary drivers, any one the opensuse or fedora should work, it really depends on what type of install package is in that .tar.bz2 package so extract/unpack the tar.bz2 package and tell us whats inside.

---

### Post by jsvannorman on 2010-12-24
Thanks!  I extracted each and it looks like they are all Alsa drivers (which is the default driver Ubuntu installs, right?).  

The reason I was wanting to use a different driver is that I noticed that there was no surround sound option for digital on the default driver, only stereo, and I'd rather use digital surround sound than analog (which is an option).  Now I'm wondering if the digital provides the full signal for my stereo receiver to do surround sound, even though the sound preferences on Ubuntu only says it is a digital stereo output.

Of course, if that isn't the case and anyone knows of a way to run 7.1 digital sound, let me know.  

John

---

