---
title: "Compiz + ATI help"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by abeautifulplace on 2009-03-22
Hello,
I'm trying to use Compiz on my install of Ubuntu 8.10. When I try to enable desktop effects, It says they cannot be enabled.
The results of Compiz-Check:
```

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Rage Mobility M4 AGP
 Driver in use:         Unknown
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 

```
Any idea on how I can get this to work?
Thanks in advance ;)

---

### Post by 73ckn797 on 2009-03-22
It looks like you will need to enable restricted drivers for the video card.

You will need to go to System/Administration/Software Sources and enable restricted repositories. You will have to reload the sources after this. 

Then go to System/Administration/Hardware Drivers and select the recommended driver.

---

### Post by abeautifulplace on 2009-03-22
> **73ckn797 said:**
> It looks like you will need to enable restricted drivers for the video card.

You will need to go to System/Administration/Software Sources and enable restricted repositories. You will have to reload the sources after this. 

Then go to System/Administration/Hardware Drivers and select the recommended driver.

There's nothing under Software Sources that enables restricted repositories. (well, If there is I can't find it)
When I click on Hardware Drivers, It searches for drivers for a few minutes and remains at 0%.

---

### Post by skymera on 2009-03-22
Install Envy from Synaptic.

Use that for ATi

---

### Post by abyssius on 2009-03-22
> **abeautifulplace said:**
> Hello,
I'm trying to use Compiz on my install of Ubuntu 8.10. When I try to enable desktop effects, It says they cannot be enabled.
The results of Compiz-Check:
```

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Rage Mobility M4 AGP
 Driver in use:         Unknown
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 

```
Any idea on how I can get this to work?
Thanks in advance ;)

Unfortunately, there is no ATI Linux driver for Rage chipsets - Only Raedon chipsets are supported. You probably won't be able to run Compiz with that video chipset.

---

