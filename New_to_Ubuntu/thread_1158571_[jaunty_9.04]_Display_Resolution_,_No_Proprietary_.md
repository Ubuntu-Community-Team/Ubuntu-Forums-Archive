---
title: "[jaunty 9.04] Display Resolution , No Proprietary Drivers"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by xioustic on 2009-05-13
Hello all,

I have a frankensteined together desktop machine running the newest version of MythBuntu for x86. I have everything working so far EXCEPT the display resolution will only allow for 640x480 and 800x600. Obviously I would like this to be much higher, and eventually a widescreen display for a widescreen flatscreen TV I have setup.

I've done this before on older versions of MythBuntu on a near identical machine with no issues so I assume this is a Jaunty related issue. The video card is a Radeon x800. This would normally require (I assume) proprietary drivers to run correctly. Under Hardware Drivers, there is no such entry for an ATI card.

It appears xorg.conf use has been stripped in this new version of Ubuntu so the old fixes I'm used to running through have been rendered /dev/null.

I'm not sure what information to give from here.

In summary: Hey, my monitor only is allowing for up to 800x600 and my video card doesn't look like it's getting detected correctly.

Thanks for the help!

EDIT: Also, my problem appears to have the same symptoms as the one listed recently here: [http://ubuntuforums.org/showthread.php?t=1149469](http://ubuntuforums.org/showthread.php?t=1149469)

---

### Post by CatKiller on 2009-05-14
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

