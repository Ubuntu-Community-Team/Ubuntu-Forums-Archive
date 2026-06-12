---
title: "Resolution"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by Azzazil on 2009-09-02
Hi yesterday I install Ubuntu and I have problems with my resolution I try everyting 
When I want change my resolution in display options I can not change because it is limited just for 800x600 and when i install driver for nivdia geforce mx 440 I have the same problem.
 
I hope that you are understand me and my english.

---

### Post by sydbat on 2009-09-02
> **Azzazil said:**
> Hi yesterday I install Ubuntu and I have problems with my resolution I try everyting 
When I want change my resolution in display options I can not change because it is limited just for 800x600 and when i install driver for nivdia geforce mx 440 I have the same problem.
 
I hope that you are understand me and my english.What version of Ubuntu are you using? 9.04?

---

### Post by Azzazil on 2009-09-02
> **sydbat said:**
> What version of Ubuntu are you using? 9.04?
 
yes

---

### Post by NoaHall on 2009-09-02
System -> Admin -> Hardware Drivers
find and install your driver.

---

### Post by CatKiller on 2009-09-02
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

### Post by dumblebee100 on 2009-09-02
> **Azzazil said:**
> Hi yesterday I install Ubuntu and I have problems with my resolution I try everyting 
When I want change my resolution in display options I can not change because it is limited just for 800x600 and when i install driver for nivdia geforce mx 440 I have the same problem.
 
I hope that you are understand me and my english.

after installing necessary drivers even though if you dont get proper resolution then you have to edit your xorg.conf file 

you should add different modes for it to get different modes of resolution

---

### Post by Azzazil on 2009-09-02
> **CatKiller said:**
> Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

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

I was modified 
[HTML] HorizSync       
        VertRefresh     [/HTML]
to 30-70 and 50-160 
and save then i restart computer but I wasn't change anything  :(

---

### Post by socool274 on 2009-09-02
Install graphics drivers. If you have nvidia/ati, you should use the nvidia driver. Nvidia is easy to get in ubuntu. System -> Administration -> Hardware Drivers. It should list available drivers. Look for a graphics driver, install, and restart. If restarting did not change the resolution, then go to System -> Preferences -> Display. Change the resolution. If this doesn't work, then I don't know the solution.

---

### Post by Azzazil on 2009-09-02
[http://i32.tinypic.com/s5id92.png](http://i32.tinypic.com/s5id92.png)
[http://i25.tinypic.com/xd9tzo.png](http://i25.tinypic.com/xd9tzo.png)

---

### Post by Azzazil on 2009-09-02
> **socool274 said:**
> Install graphics drivers. If you have nvidia/ati, you should use the nvidia driver. Nvidia is easy to get in ubuntu. System -> Administration -> Hardware Drivers. It should list available drivers. Look for a graphics driver, install, and restart. If restarting did not change the resolution, then go to System -> Preferences -> Display. Change the resolution. If this doesn't work, then I don't know the solution.


I was install nvidia drivers on "Hardware Drivers" I set "Active" and install drivers
In Display I can't change resolution because it's still limited on 800x600

---

### Post by CatKiller on 2009-09-02
> **Azzazil said:**
> I was modified 
[html] HorizSync       
        VertRefresh     [/html]to 30-70 and 50-160 
and save then i restart computer but I wasn't change anything  :(

Sometimes monitors report incorrect EDID values rather than none at all. In those cases, putting ```
        Option          "UseEDID"                       "False"
```in the Device section will tell X to ignore any information from the monitor and just use the values you've given it.

---

### Post by Azzazil on 2009-09-02
> **CatKiller said:**
> Sometimes monitors report incorrect EDID values rather than none at all. In those cases, putting ```
        Option          "UseEDID"                       "False"
```in the Device section will tell X to ignore any information from the monitor and just use the values you've given it.

Dude thanks I must buy you a beer It works finally

---

### Post by dumblebee100 on 2009-09-09
u can see my xorg.conf and can get some idea why u r facing problems ..

earlier I used to have resolition problems with intel graphics driver ...but after using this configuration file I now have 1440x1050 resolution and my movies and other stuff like compiz works perfect ..
after adding horizontal and vertical refresh things and modelines and modes in my xorg.conf then my xserver works good 
```
# xorg.conf.failsafe (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS"
	HorizSync	30-71
	VertRefresh	50-160
Modeline "1400x1050_60.00"  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
Modeline "1152x864_60.00"   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync

EndSection

Section "Screen"
	Identifier "Default Screen"
	Device "Configured Video Device"
	Monitor "Configured Monitor"
	DefaultDepth 24
	SubSection "Display"
	Depth 24
	Modes "1400x1050" "1280x1024" "1152x864" "1024x768"
	EndSubSection
EndSection
```

---

