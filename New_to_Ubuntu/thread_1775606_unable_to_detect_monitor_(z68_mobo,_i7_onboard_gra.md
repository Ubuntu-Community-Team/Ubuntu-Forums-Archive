---
title: "unable to detect monitor (z68 mobo, i7 onboard graphics, 64bit)"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by NewbuntuUser777 on 2011-06-05
New machine running i7 2600k sandy bridge onboard graphics on z68 chipset (Asrock mobo), 10.04 64bit ubuntu, and I'm unable to get monitor working right.

I'm able to get a very close resolution of 1600x1200, but my actual resolution is 1680x1050 (the 1600x1200 looks real bad).

32bit versions of debian 6 and ubuntu 10/11 have no problem with resolution/finding monitor but don't detect my ram.  

Ubuntu 11 64bit (and Fedora 15 64bit) both recognize the acer monitor and get the right resolution but are totally unstable (I'm not able to get through an install but can boot into live CD for a little while, not very long).

I did try adding a 1680x1050 newmode with xrandr, but that trashed my install and I had to re-install to get up and running again.

This is annoying because I know that somewhere between 10.04 and 11.04 the issue with the monitor was solved, but I'm unable to run 11.04 so it's no help to me.

Bottom line: I need all my ram (16gb), and I need proper resolution/graphics without having to buy a graphics card to get there (this was the main reason I bought the z68 mobo).  Anything that gets me there without having to buy a graphics card or purchase windows is acceptable to me.

Any help or suggestions are appreciated.  If there are other forums you think might be helpful let me know.

Thanks!


Update:  I am also unable to turn on visual effects; "Desktops effects could not be enabled"

---

### Post by NewbuntuUser777 on 2011-06-05
Bump.

---

### Post by NewbuntuUser777 on 2011-06-05
Update: I've solved the resolution issues by doing an upgrade through the update manager, moving up to 10.10 64 bit from 10.04 64 bit.

I'd love to better understand why I was having problems and what it is about 10.10 that solved them, but at least I'm up and running now.

For those considering going with z68 north bridge and sandy bridge graphics, do it!

---

### Post by topet2k12001 on 2011-07-28
> **NewbuntuUser777 said:**
> Update: I've solved the resolution issues by doing an upgrade through the update manager, moving up to 10.10 64 bit from 10.04 64 bit.
 
I'd love to better understand why I was having problems and what it is about 10.10 that solved them, but at least I'm up and running now.
 
For those considering going with z68 north bridge and sandy bridge graphics, do it!
 
Hi Friend,
 
May be too late for a reply, but...if your goal is to be able to use all RAM, you could try using a PAE Kernel (you can find it from Synaptic Package Manager). Using a PAE Kernel allows you to use 4GB RAM (and up) in a 32-bit version of Ubuntu. In any case I was able to read from the Ubuntu website that they recommend using 32-bit so I really didn't bother trying a 64-bit version (this, especially written when I tried out Ubuntu 10.04).
 
Nevertheless it's nice to hear that you got your system up and running. :) I'm looking forward to upgrade soon and trying to learn which hardware (H- P- or Z-board with Intel i-series processor) to purchase.

---

### Post by then_dude on 2011-08-08
i got the same setup

an asrock z68 , i2500k and crucial m4, 8gb ram

i have tried a lot : 10.04, 10.10, 11.04 ; all 32 bit versions. 

the 11.04 and the 10.10 was slow, very slow compared with the 10.04: which is lightning fast. 

but on the 10.04 i can only see 1280*1024 (the max of the vesa driver)

i have run with the 11.04 and the pae kernel, but that was not that stable; 

strange that everybody system is different although it has the same components. 

maybe i need to get my hands on the 64 bit version. but what about the apps, do they run as good on the 64 bit as the 32 ?

thanks

---

### Post by CatKiller on 2011-08-09
Why are you using the vesa driver?

Applications run fine on 64-bit.

---

