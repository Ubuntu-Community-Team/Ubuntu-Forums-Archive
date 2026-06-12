---
title: "Problem installing ipw2200 ieee80211 subsystem"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by ubuntu_jazzbach on 2007-01-17
Hi !!!

I just updated the kernel to 2.6.19 (Edgy Eft) because I wanted to improve some graphic aspects. The thing is that when I updated, the wireless driver wasn't installed. I had installed that driver previously so, I didn't think I'd encounter problems during that process (ja, ja, ja !!! how naive I am :) ) 

So now I want to install the ipw2200 driver. Previous to this, I know I gotta have the firmware and the ieee80211 subsystem. I had no problem setting up the firmware but, when installing the ieee subsystem the following error occurs:

/bin/sh: Syntax error: "(" unexpected
make: *** [check_old] Error 2

What am I doing wrong !!!!!  PLEASE HELP !!!

---

### Post by ubuntu_jazzbach on 2007-01-17
PLEASE !!!! PLEASE !! a little help here !!!  :(

---

### Post by drvdw on 2007-01-22
I compiled and installed a new kernel from ubuntu 2.6.17.14 kernel source.  At first I tried to do an out of tree compile for ipw2200 and ieee80211 but I was getting that problem too.  Then I just selected ieee80211 and ipw2200 from menuconfig and compiled them with my kernel.  After that I copied all the firmware into a new directory in /lib/firmware:
 ```

cp -a /lib/firmware/2.6.17-generic /lib/firmware/`uname -r`
```

And now it works fine.

---

