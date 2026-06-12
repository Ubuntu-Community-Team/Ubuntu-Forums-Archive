---
title: "Installing a video card driver"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by Strider11o7 on 2009-06-16
I'm currently using a ATI Mobility Radeon HD 4570 on 8.10 and trying to figure out how to install drivers for it because it isn't available in Hardware Drivers menu. I've read a couple help guides but they haven't been very helpful =/

Any help would be appreciated.

---

### Post by sandyd on 2009-06-16
> **jonaz said:**
> 
You can download working drivers for the 4570 from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx ]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")

to install them go to where you saved them and type:

sudo sh ./ati* --listpkg

this will give you instructions on how to build custom packages for your distro
for Ubuntu/8.04 this is:

sudo sh ./ati* --buildpkg Ubuntu/8.04

after this 6 new packages should be created: just install them all with synaptic, enable your driver in Hardware Drivers and reboot.

taken from [http://ubuntuforums.org/showthread.php?t=1114683](http://ubuntuforums.org/showthread.php?t=1114683)

---

### Post by Strider11o7 on 2009-06-16
Okay, i'm at the last step, where in synaptic would they be located, or what their package names would be?

---

### Post by shifty_powers on 2009-06-16
what was the terminal output of the last command?

---

### Post by Strider11o7 on 2009-06-16
Oh i'm not certain, I thought it was successful because my desktop had 6 new packages available to install, so I just installed them each from there. Still no available Hardware Driver though =/

---

### Post by Strider11o7 on 2009-06-16
Ok I just did it again:

```
Generating package: Ubuntu/8.10
Package /home/eric/Desktop/xorg-driver-fglrx_8.620-0ubuntu1_i386.deb has been successfully generated
Package /home/eric/Desktop/xorg-driver-fglrx-dev_8.620-0ubuntu1_i386.deb has been successfully generated
Package /home/eric/Desktop/fglrx-kernel-source_8.620-0ubuntu1_i386.deb has been successfully generated
Package /home/eric/Desktop/fglrx-amdcccle_8.620-0ubuntu1_i386.deb has been successfully generated
Package /home/eric/Desktop/fglrx-modaliases_8.620-0ubuntu1_i386.deb has been successfully generated
Package /home/eric/Desktop/libamdxvba1_8.620-0ubuntu1_i386.deb has been successfully generated
Removing temporary directory: fglrx-install.o19938

```

---

### Post by Strider11o7 on 2009-06-16
Nvm, I finally got it to work, thanks!

---

### Post by shifty_powers on 2009-06-16
you should be able to

```
cd ~/Desktop
sudo dpkg -i *.deb
```

(i'm away from my ubuntu machine, so apologies if the dkg code is not quite right. plus don't forget to reboot).

---

