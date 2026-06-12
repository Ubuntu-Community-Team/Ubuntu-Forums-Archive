---
title: "ATi Radeon HD4870"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by SolidusRegime on 2009-06-17
I have just installed Ubuntu onto my new machine and am unable to get visual effects working at all.

I have read numerous threads about the lack of working ATi drivers, but they all say different things and I am really confused.

Could someone, with the same card who got everything work correctly, possible point me in the right direction?

Thanks in advance.

---

### Post by estyles on 2009-06-17
Try installing ubuntu-restricted-extras, if you haven't already.  You can either go to the menu under Administration or Preferences and look for Hardware Drivers, or else open Synaptic and search for fglrx or ubuntu-restricted-extras.

If that doesn't help, then it may be a more annoying problem to deal with...

---

### Post by SolidusRegime on 2009-06-17
There is only 1 proprietary driver to install under there and that is for my wireless card. I'm beginning to wonder if 3D support is functional at all.

---

### Post by estyles on 2009-06-17
I haven't heard about any problems with the 4870 - should work fine.  Try installing ubuntu-restricted-extras from synaptic or Add/Remove.  You're gonna want some of the other stuff in there anyway.

Also, look for fglrx in synaptic, and make sure that installs.

---

### Post by alienkid10 on 2009-06-17
find your card here:[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) download the file then follow install instructions. then run aticonfig --initial in a terminal. Reboot then got to CCC in applications -> other (not the super user one) click display manager then click the magnifying glass then configure it. Click ok then done. I just set up my hd4350 after weeks of stuggling that way

---

### Post by SolidusRegime on 2009-06-18
> **alienkid10 said:**
> find your card here:[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) download the file then follow install instructions. then run aticonfig --initial in a terminal. Reboot then got to CCC in applications -> other (not the super user one) click display manager then click the magnifying glass then configure it. Click ok then done. I just set up my hd4350 after weeks of stuggling that way

I will have to test this out tonight. Are any other packages needed before I install CCC?

---

### Post by waspbr on 2009-06-18
nope, though ATI has been dropping the ball on the drivers for a while now... I still cannot enabled desktop effects on my HD 3300

---

### Post by SolidusRegime on 2009-06-18
I am hoping someone with a HD4870 can post here as I have read numerous ways to fix the ATi display drivers, but none were specified for my type of card.

EDIT: I just followed your guide alienkid, and it worked fine, although not only are the effects are very pixelated, my computer crashes when a full screen video is played and maximizing/minimizing windows has a 1-2 second delay.

---

### Post by microft on 2009-06-25
I have a HD4870 running on Ubuntu 9.04. It's working fairly well with the latest ATI drivers (9.6). 

I used the binary from ATI's site to generate the .deb files to install.

Some things are still slow (like resizing windows), but desktop effects work. No video flickering.

---

