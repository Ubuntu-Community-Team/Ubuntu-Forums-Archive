---
title: "What is an 'Unclaimed' Device?"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by DeanoCYM on 2009-06-24
Hi,

I'm using an old compaq nc6000 with an ATI Mobility Radeon 9600 graphics card. When I run:
```
 lshw -C display 
```
I get:
```
  *-display UNCLAIMED
       description: VGA compatible controller
       product: RV350 [Mobility Radeon 9600 M10]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm bus_master cap_list
       configuration: latency=64 mingnt=8 
```

Does this mean the driver isn't installed? If so would I just download a propriety one from ATI? Any help would be much appreciated.

Thanks in advance,
Rhys.

---

### Post by DeanoCYM on 2009-06-25
(cheeky bump)

---

### Post by grog808 on 2009-06-26
From my (limited) experience, ATI support for linux is poor at best.  If you're trying to mess with your screen resolution, you can try playing with /etc/X11/xorg.conf.  There's lot's of parameters that go in there with some particular syntax, so be careful when editing.  Be sure to back it up before you start, and be prepared to restore it...

---

### Post by sim-value on 2009-06-26
I think its nothing to worry about i get an Unclaimed Device on all my PCs

Do you have 3D acceleration ?

---

### Post by DeanoCYM on 2009-06-26
> **sim-value said:**
> I think its nothing to worry about i get an Unclaimed Device on all my PCs

Do you have 3D acceleration ?

glxinfo tells me that I have direct rendering, I guess this means everything is ok. Shame I cant get a new GPU tbh could really do with a bit extra power there, everything else is great. Well thanks for the help everyone.

Rhys

---

