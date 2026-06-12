---
title: "Changing resolution 9.04"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by Sexraider on 2009-07-10
I have a HP w19 19" LCD widescreen monitor and Apperantly ubuntu isn't picking it up as a monitor so, is there drivers for this? how can I change the resolution.

---

### Post by cozmicharlie on 2009-07-10
Do you know what type of video card you have (NVIDIA or AMD)?  If you go to System>Administration>Hardware Drivers is any driver listed?

---

### Post by CatKiller on 2009-07-11
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

According to [this page]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00655671&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN"), the values you want are

```

         HorizSync       30-83
         VertRefresh    55-75

```

---

