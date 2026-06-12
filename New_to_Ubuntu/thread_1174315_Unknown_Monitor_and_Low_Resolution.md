---
title: "Unknown Monitor and Low Resolution"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by Tricause on 2009-05-30
Hi,

This is my first time using Ubuntu and I am experiencing some really annoying problems. After searching the internet for solutions, I found relatively little that could help me. 

I am currently running a low resolution at 1024 x 768 instead of the 1440 x 900 I can run easy on windows. My display is consequently stretched. When I go to change the display, it will not allow me to go any further in resolution and furthermore says that my monitor is unknown.

I have a 19" Samsung SyncMaster 941BW monitor. My video card is a GeForce 7600 GS. 

My abilities with Ubuntu are relatively low. I know how to access Terminal, but that is about it. I would like to know a way to have my monitor "known" and for the resolution is to be fixed.

Thanks for any help.

---

### Post by kingnerd on 2009-05-30
Sounds like you are missing the NVidia driver for your graphics card.   Check System -> Administration -> Hardware Drivers and see if it recommends installing it.

---

### Post by CatKiller on 2009-05-30
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

According to the manual that I found on the Samsung site, the values you're looking for are

```
        HorizSync       30-81
        VertRefresh     56-75
```

---

### Post by Tricause on 2009-05-30
Thanks for the help. The problem for me was the lack of drivers and I found out that I one of my cables to my video card got disconnected. I did not have to edit my xorg.conf, although if I have a problem with a future monitor, I should now know how to deal with it.

Thanks again for the help.

---

### Post by CatKiller on 2009-05-31
Glad you got it sorted.

---

