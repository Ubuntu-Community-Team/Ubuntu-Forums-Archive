---
title: "Intrepid and GeForce Nvidia"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by pearlbeer on 2008-12-16
I installed intrepid and used envy to get the display 'working'. Everything seems to work ok now, except 3d stuff (awn compiz etc). Tried switching to the beta drivers (180.16) and there is no difference. Card is a GeForce 6200. Any suggestions?

---

### Post by starcannon on 2008-12-16
Heres a little guide I wrote:
[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

That should get you where you wanna be.

---

### Post by pearlbeer on 2008-12-16
Thanks for the guide. I tried it, and it did install the 180.16 again, but the 3d effects are still not working. they were working on previous version. thanks anyway.

---

### Post by starcannon on 2008-12-16
I am using the 177.82 driver and its working excellently on my 6600gt, my 7950gt dual card sli setup, and on this 8400m gs.
177.82 is the latest stable release driver, you appear to be playing with a beta driver. If you want it to "just work" then grab the latest stable here:
[http://us.download.nvidia.com/XFree86/Linux-x86/177.82/NVIDIA-Linux-x86-177.82-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/177.82/NVIDIA-Linux-x86-177.82-pkg1.run)

GL and have fun

---

### Post by pearlbeer on 2008-12-16
I'll try that.

---

### Post by pearlbeer on 2008-12-16
I swapped back to the 177 stable. Same thing. Could I actually be running off the original on-board card rather than the nvidia card? how can i tell in linux land?

---

### Post by JoshuaRL on 2008-12-16
Well, which set of outputs do you have your monitor connected to?  Is it the one right off of the mainboard or is it from the PCI/AGP port?

---

### Post by pearlbeer on 2008-12-16
awww, hell. been drinkin too much tonight. forgot about the damn outputs. i am definitely connected to the nvidia. forget i asked that.

---

### Post by starcannon on 2008-12-16
> **pearlbeer said:**
> I swapped back to the 177 stable. Same thing. Could I actually be running off the original on-board card rather than the nvidia card? how can i tell in linux land?

Run these commands:
```

glxinfo | grep server
sudo lshw -C display

```
post output here.
Be sure to turn off the onboard video chipset in bios as well, this way you know it can't be conflicting.

---

### Post by starcannon on 2008-12-16
> **pearlbeer said:**
> awww, hell. been drinkin too much tonight. forgot about the damn outputs. i am definitely connected to the nvidia. forget i asked that.
bahahaha.... lolz.... hate it when that happens *hic*

---

### Post by pearlbeer on 2008-12-16
you'll have to remind me how to blacklist the old card..

pat@pat-desktop ~ $ glxinfo | grep server
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
pat@pat-desktop ~ $ sudo lshw -C display
[sudo] password for pat: 
  *-display UNCLAIMED     
       description: Display controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
  *-display
       description: VGA compatible controller
       product: NV44A [GeForce 6200]
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:01:05.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia

---

### Post by starcannon on 2008-12-16
The easiest way is to disable the onboard gpu in bios, press setup key at boot, should be a message telling what it is:
Del
F2
or whatever the manufacture decided on. watch for the message when you first turn on the machine, be quick with the pause key and you can catch it before it disappears.

GL

---

### Post by pearlbeer on 2008-12-16
really appreciate your time and effort on this...only options in bios are "auto" and "on board".. it's on auto.

and, fwiw, i am pretty much fully functional (no flash/video problems) with the exception of the 3d stuff. cant remember what i did in hardy to make it work, but it did.

---

### Post by JoshuaRL on 2008-12-16
The problem with setting BIOS like that is that often Linux doesn't care.  You see, BIOS is supposted to pass system info to the OS.  But Linux prefers to do it's own hardware detection.  So you may need to blacklist the Intel driver.  First, figure out what driver is the one you don't want.  Then:
```

gksu gedit /etc/modprobe.d/blacklist

```
Then add the name of the driver in there.  Save and quit Gedit.  That will keep it from being added to the kernel at boot time.  Then:
```

modprobe -r (driver)

```
to take that driver from the kernel.

---

