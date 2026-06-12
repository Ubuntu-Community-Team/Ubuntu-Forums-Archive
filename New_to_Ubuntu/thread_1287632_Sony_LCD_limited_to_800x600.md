---
title: "Sony LCD limited to 800x600"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by hotbelgo on 2009-10-10
Hi,
I had this with 9.04 and 9.10 is no better.  The X settings for my NVidia 5200fx with a Sony SDM HS75B LCD screen do not offer a 1028x768 resolution.

Previously I copied the xorg.conf file that Mandriva created but I just zapped my old disk.  Anyway, there is no xorg.conf in 9.10.

What can I do to get ubuntu to get the most from my card.  It is even worse with the nvidia drivers (max 600x480).

HB

---

### Post by ibuclaw on 2009-10-10
Sounds like the EDID for your monitor is either none-existent or the checksum is giving X.org an incorrect value.

Using the NViDIA drivers, try pressing **Alt+F2** and type in:
```
gksudo nvidia-settings
```
And see if you can change the resolution there and save.

If not, run:
```
sudo nvidia-xconfig
```
in a terminal and logoff/logon.

If the resolution still is being persistently low, then as a last resort, up the value of the HorizRefresh in your xorg.conf file.

```
gksudo gedit /etc/X11/xorg.conf
```
you should be able to see something like:
```

     HorizSync       28.0 - 33.0
     VertRefresh     43.0 - 72.0

```

For most systems I have tested, these values usually work.

For standard monitors, change it to:
```

     HorizSync       28.0 - **60.0**
     VertRefresh     43.0 - 72.0

```

For widescreen monitors, change it to:
```

     HorizSync       28.0 - **75.0**
     VertRefresh     43.0 - 72.0

```
Although, do bare in mind that for older monitors, there could be drastic effects from changing this value in the event of EDID not properly detected. Such could include damaging your monitor indefinitely.

Regards
Iain

---

### Post by sandyd on 2009-10-10
try downloading the drivers from nvidia. 
thats what i did for my 5500.

---

### Post by hotbelgo on 2009-10-11
> **tinivole said:**
> Sounds like the EDID for your monitor is either none-existent or the checksum is giving X.org an incorrect value.


Indeed, I discovered this
```
(WW) NVIDIA(GPU-0): The EDID read for display device CRT-0 is invalid:
(WW) NVIDIA(GPU-0):     unrecognized EDID Header.

```

and

```
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:E-EDID segment register" registered at address 0x60.
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 appears to have a CRT attached

```

in my logs.  It seems Mandriva does not use edid to set itself up and that's why it produces a better result.

If I can find my windows disks I'll install that and see whether the card is bust in that OS too.

---

### Post by CatKiller on 2009-10-11
As tinivole says, normally resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

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

According to the manual, that I got from [this page]("http://esupport.sony.com/US/perl/model-documents.pl?mdl=SDMHS75B"), the values you need are

```
         HorizSync       28-80
         VertRefresh     48-75
```

---

