---
title: "trouble with VT8375 [ProSavage8 KM266/KL266] help please"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by mask187 on 2009-02-06
hi I am using ubuntu 8.10 intrepid ibex I have tried a few things including xorg configure and messing with the xorg file directly with no luck there is no driver for it and I would like to at lest increase resolution from 800/600 to 1280/1240 is that possible?

---

### Post by mask187 on 2009-02-06
here is the xorg.conf file hope it helps

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
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

### Post by mask187 on 2009-02-06
typed
```
lspci | grep VGA
```

got

```
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
```

then
```
sudo lshw -C video
```

got

```
 *-display UNCLAIMED     
       description: VGA compatible controller
       product: VT8375 [ProSavage8 KM266/KL266]
       vendor: S3 Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 bus_master cap_list
       configuration: latency=32 maxlatency=255 mingnt=4

```

---

### Post by mask187 on 2009-02-06
bump

---

### Post by mask187 on 2009-02-06
bump

---

### Post by waleedakleh on 2010-01-11
same problem need help

---

