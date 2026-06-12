---
title: "NVIDIA 5200 FX Resolution"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by sim-value on 2009-03-22
Hi a friend of mine got an NVdia 5200 FX card...

Now the card works well under XP but in Ubuntu It does not ...

The resolution in the NVIDIA Controll Panel can be set max. too 640x480 ...

In the Screen Resolution Panel it can be set too 1024x768 but he cant apply cause he doesnt see the Apply Button ... 

Can somebody please tell me how to Edit the Xorg.conf for a res. of 1024x768?

Or just how many times you have to press tab until you are on the Apply Button in Ubuntu 8.10 (its different than in 8.04) ?

/me

---

### Post by taurus on 2009-03-22
Look in System -> Administration -> Hardware Drivers to see if there is a recommended nvidia driver for that graphic card.

---

### Post by sim-value on 2009-03-22
Yes thats the one he installed

---

### Post by sandyd on 2009-03-22
i used envyng for that...

```

sudo apt-get install envyng-core
envyng -t

```

make sure you run that after pressing Ctrl+alt+F1
also make sure you install the recommended driver.

---

### Post by overdrank on 2009-03-22
Hi and if you can not see the apply button you may use the alt, and single click with the mouse to move the window. Also you may try the ```
gksu nvidia-settings
```

---

### Post by txcrackers on 2009-03-22
If I remember correctly, the 5200 series needs to use the NVidia "legacy" driver.

---

### Post by abyssius on 2009-03-22
I'm using an NVIDIA 5200FX with the NVIDA-Linux-x86_173.14.16 beta driver from NVIDIA with no problems to report. I think the 173 driver provided with 8.10 would be fine. I also had the low resolution problem when I first installed the NVIDIA driver. It turned out that the problem wasn't caused by the driver, it was because the X server didn't properly detect my monitor. All I had to do was to insert the correct horizontal sync and vertical refresh values and my desired resolution in my xorg.conf file to correct this problem. I think this is the simplest way. 

```

Section “Monitor”
Identifier    “Configured Monitor”
HorizSync       30-81
VertRefresh     60
EndSection

Section “Screen”
Identifier    “Default Screen”
Monitor        “Configured Monitor”
Device        “Configured Video Device”
DefaultDepth    24
SubSection      “Display”
Depth           24
Modes           “1920×1200_60&#8243;
EndSubSection
EndSection

```

Of course, the HorizSync, VertRefresh and Modes values should be changed to match the actual monitor being used.

---

