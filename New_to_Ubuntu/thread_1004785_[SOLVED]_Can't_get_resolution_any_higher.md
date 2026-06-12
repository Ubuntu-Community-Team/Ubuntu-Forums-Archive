---
title: "[SOLVED] Can't get resolution any higher"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by CycleLock on 2008-12-07
Using Ubuntu 8.10
Video Card: Nvidia Geforce FX 5200 rev. a1
Monitor: Mitsubishi Diamond Scan 17FS

Using the the drivers that installed by default I can't get a higher resolution then 800x600. If I install the restricted driver for Nvidia (173) I can't get a higher resolution then 640x480. 

Help!
Thanks in advance.

---

### Post by LowSky on 2008-12-07
run ```
gksu nvidia-settings
```

---

### Post by CycleLock on 2008-12-07
Went to 'X Server Display Configuration' Clicked Advanced and typed in 1024x768. It kept CRT-0 screen resolution at 640x480 but expanded the desktop to 1024x764. (it filled in the 'Panning' setting.) 

The highest resolution I can select is 640x480.

---

### Post by CycleLock on 2008-12-10
My latest theory is that the EDID from the monitor is not being read and I need to manually put that into the xorg.conf file.

Thread where I found this theory.
[http://www.nvnews.net/vbulletin/showthread.php?t=116515](http://www.nvnews.net/vbulletin/showthread.php?t=116515)

Threads mentioned in the thread above for fixing this.
	[http://myricci.com/index.php?option=com_content&task=view&id=36&Itemid=9](http://myricci.com/index.php?option=com_content&task=view&id=36&Itemid=9)
	[http://www.thinkwiki.org/wiki/Installing_Gentoo_2007.0_on_a_ThinkPad_R61#xorg.conf](http://www.thinkwiki.org/wiki/Installing_Gentoo_2007.0_on_a_ThinkPad_R61#xorg.conf)

I will keep you updated.

---

### Post by northern lights on 2008-12-10
Run ```
nvidia-xconfig
``` once and thereupon try to set your settings with *nvidia-settings*. Should you still not get the results you wished for, try either to fix things with ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and/or post the output of ```
sudo lshw -C display
```

---

### Post by CycleLock on 2008-12-14
lock@lock-desktop:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: NV34 [GeForce FX 5200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 bus_master cap_list
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia

---

### Post by evilkastel on 2008-12-14
i had that exact issue on a similar nvidia card. here is how i fixed it. dull process. worked. :).

[http://ubuntuforums.org/showthread.php?t=966489](http://ubuntuforums.org/showthread.php?t=966489)

---

### Post by northern lights on 2008-12-15
> **CycleLock said:**
> lock@lock-desktop:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: NV34 [GeForce FX 5200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 bus_master cap_list
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
The correct driver appears to be assigned. Have the issues been sorted?

---

