---
title: "low video resolution intel integrated graphics"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by go4thaudio on 2009-07-07
I have a very low resolution of 800x600.  lsci gives me 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE chipset Integrated Graphics Device (rev 01)   My monitor is a Hitachi SuperScan Elite 20.  The resolution is so poor that I can't even fully view the windows in 'Ardour' they won't drag around correctly.  What should I do.  I am a newbie so take it one step at a time, please.

---

### Post by cariboo on 2009-07-07
What version of Ubuntu are you using? If you are using Jaunty (9.04) then have a look at this [sticky]("http://ubuntuforums.org/showthread.php?t=1130582").

---

### Post by CatKiller on 2009-07-08
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

According to [this page]("http://www.monitorworld.com/Monitors/nsahitachi/superscanelite20cm2098mu.html"), the values you're looking for are

```
        HorizSync       30-90
        VertRefresh     50-150

```

---

