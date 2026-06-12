---
title: "Video Card Issues!"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by economy on 2008-12-26
[LEFT][Hi all,

This is partly my own ignorance of my machine, and partly serious.

I have an HP dv6000 on which Hardy Heron is the only OS. I had Vista on here when the laptop was purchased, didn't take long for me to get fed up with that.

I cannot get 3d acceleration working, and I have no drivers listed in my Hardware Drivers menu. Either Ubuntu doesn't recognize my video card, or it's onboard VGA, which I doubt, because Vista ran 3d accelerated games without issue. 

I installed EnvyNG and it cannot find the card either.

Here's some outputs that may be useful:

economy@economy:~$ lshw -C display
WARNING: you should run this program as super-user.
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
economy@economy:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
economy@economy:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual]
[/LEFT]
thanks in advance for your help,

---

### Post by taurus on 2008-12-26
I thought envyNG only supports nVidia and ATI graphic cards, not an Intel integrated graphic controller.

---

### Post by economy on 2008-12-26
Right, I was under the assumption that I had an nVidia, but from all the posts I've read to date, I can't find that out! Stupid, I know... is there any way to check besides opening the casing and having a look?

---

### Post by alienexplorers on 2008-12-26
You have a Intel Mobile GM965/GL960 Integrated Graphics Controller.

---

### Post by economy on 2008-12-26
It was right there in the output... lame of me.

Any way to enable 3d acceleration using that?

I'll look into upgrading right away

---

