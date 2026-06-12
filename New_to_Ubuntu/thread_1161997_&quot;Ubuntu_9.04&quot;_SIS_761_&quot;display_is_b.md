---
title: "&quot;Ubuntu 9.04&quot; SIS 761 &quot;display is blue&quot; :("
date: 2009-05-17
forum: New to Ubuntu
---

### Post by barathbr on 2009-05-17
Hi 

Just installed Jaunty on my laptop (Acer Aspire 5002 WLMi) which had Windows on it before. The display is all screwed up now. It has shades of blue all over. Can anybody help. I am not sure where to start. Based on advice I have seen in other places in the forum, lspci | grep VGA gives this:

```
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```

xorg.conf contains this:

```

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

---

### Post by ellgor on 2009-05-17
Hi,

Go to the multimedia-video forum and follow the sticky on that subject, had trouble loading podcasts and allsorts, fixed it a treat.

Regards, Ellgor.

---

### Post by barathbr on 2009-05-19
That didn't help. I read through it and appears to be stuff related to setting up multi media apps. Not configuring it for SiS cards per se.

---

