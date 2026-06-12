---
title: "Desktop effects"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by Blackwater12 on 2009-06-02
```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV530 [Radeon X1600]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]
``````
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:71c2 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
compiz 0.7.4

```
Why won't it let me use desktop effects?

---

### Post by s.fox on 2009-06-02
Hi,

Have you tried following the advice [here]("http://forum.compiz-fusion.org/showthread.php?t=5854")?  You seem to have a similar problem with nvidea and xgl.

Hope this helps.

-Ash R

---

### Post by labinnsw on 2009-06-02
Try installing the Nvidia driver. (System >> Administration >> Hardware drivers)

Ensure that the enable check box is ticked.

---

### Post by 3rdalbum on 2009-06-02
> **labinnsw said:**
> Try installing the Nvidia driver. (System >> Administration >> Hardware drivers)

Ensure that the enable check box is ticked.

Err... ATI driver.

ATI/AMD has obsoleted several cards in Linux, so the new drivers don't work with older cards, and the old drivers don't work with the new version of Xorg that comes with Jaunty. If the Hardware Drivers program does not offer a proprietary driver for your graphics card, then DO NOT attempt to install one from the AMD website.

---

### Post by neo.patrix on 2009-06-02
I think , ATI X1600 is a legacy card now (read Primitive). What it means is that AMD/ATI is not going to release any new drivers for it. Unfortunately old existing proprietary driver for your card which used to work with Intrepid or older system ( also older version of X.Org) will not work with Jaunty (latest version X.Org). AMD/ATI has released new driver to work with latest X.Org, but most probably that driver does not support your card. 

If you want desktop effects, you should better stick with Intrepid and not upgrade to Jaunty. I near future, think about replacing your graphics-card. (I know it is bit harsh, I am stuck as well)

---

### Post by overdrank on 2009-06-02
> **Blackwater12 said:**
> [code]Gathering information about your system...

 **Distribution:          Ubuntu 8.04**
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV530 [Radeon X1600]
 Driver in use:         radeon
 Rendering method:      AIGLX



Hi and I assumed you installed the drivers via restricted drivers under system, administration. 
Have you tried booting into recovery mode and use the xfix option?

---

### Post by Blackwater12 on 2009-06-02
> **labinnsw said:**
> Try installing the Nvidia driver. (System >> Administration >> Hardware drivers)

Ensure that the enable check box is ticked.
  

I did this now it says monitor unsupported

---

### Post by labinnsw on 2009-06-03
> **Blackwater12 said:**
> I did this now it says monitor unsupported

[Try to set the refresh rate on the monitor.]("http://ubuntuforums.org/showthread.php?t=1077328") (System >> preferences >> Screen resolution)

---

