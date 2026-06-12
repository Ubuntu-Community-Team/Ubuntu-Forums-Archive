---
title: "Nvidia GForce2 Dell xps t500"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by gldfshkpr on 2009-10-01
Hi everybody,

I have an Nvidia Gforce2 graphics card installed on a Dell Dimension XPS T500.  I can't go any higher than 640x480 on the resolution through preferences.  Can someone point me in the right direction towards getting a higher resolution?  I have a Sceptre 17 inch LCD screen.  Thank you and forgive me if this is an old subject.

---

### Post by CatKiller on 2009-10-02
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

---

