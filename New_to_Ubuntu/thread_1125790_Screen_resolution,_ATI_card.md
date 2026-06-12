---
title: "Screen resolution, ATI card"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by g3k0 on 2009-04-14
Hi,
my screen resolution wont set correctly.  I have a 1680x1050 monitor that I use with my laptop closed.  It worked one time I tried it and xorg.config was exactly like this but it wont work anymore.  I have the ATI driver installed (and it was installed the one time it worked). I am stuck at 1280x800 

Any ideas??? thanks
```


Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Depth 24
		Modes "1680x1050" "1280x1024"
	EndSubSection


EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"


EndSection


```

---

### Post by skymera on 2009-04-14
How have you installed the ATi driver?

Can you not force a resolution using the control centre?

And Xorg.conf is becoming deprecated, it's not used much anymore :(

---

### Post by g3k0 on 2009-04-14
I installed the ATI driver a long time ago.  Ubuntu just asked me if I wanted to install it with an update I think.  Changing Xorg affected it once before... i dont know why I can't get it again.  Control Center and ubuntu's top resolution is 1280x800

---

### Post by CatKiller on 2009-04-15
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
```

Bear in mind that these are the values for **my** monitor. You'll need to put in the values for **your** monitor, otherwise you could well permanently damage your monitor.

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       30-95
        VertRefresh     50-160
EndSection

```

---

