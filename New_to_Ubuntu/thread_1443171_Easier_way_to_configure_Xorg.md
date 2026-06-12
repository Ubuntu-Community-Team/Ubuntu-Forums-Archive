---
title: "Easier way to configure Xorg?"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by NightwishFan on 2010-03-30
Summary:
My friend has a card that I believe is supposed to use the OpenChrome driver. However he only gets a resolution of 800x600. I am quite sure it is possible to configure xorg to get a higher resolution but configuring that thing never gets along with me. Any tutorial I read is always specifc to ATI or Intel and any of my generic configurations simply have no effect on the resolution. Is there a graphical utility to probe and set up Xorg, or at least a simple slap on solution to enable a specific resolution for the machine?

I really have no idea how to wizard with Xorg and frankly I do not want to know how, I am just hoping to make my friends screen usable could you please help me. I went through half of the Ubuntu wiki and documentation before I posted.

Here is the output of lshw:
```
description: VGA compatible controller
       product: KM400/KN400/P4M800 [S3 UniChrome]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32 mingnt=2
       resources: memory:e4000000-e7ffffff(prefetchable) memory:e8000000-e8ffffff memory:e9000000-e900ffff(prefetchable)
```

---

### Post by halitech on 2010-03-30
not sure if you've seen this link or not

[http://ubuntuforums.org/showthread.php?t=1340466](http://ubuntuforums.org/showthread.php?t=1340466)

if that doesn't help, you'll need to edit /etc/X11/xorg.conf manually with this

```
Section "Device"
	Identifier	"Configured Video Device
	Driver		"trident"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS" "true"
	HorizSync	30.0-60.0
	VertRefresh	50.0-70.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection	"Display"
			Depth		24
			Modes		"1024x768" "800x600"
	EndSubSection

EndSection
```

---

### Post by wojox on 2010-03-30
They should just be able to go into System > Preferences > Display and set their resolution. That's all I've used on anything non-nvidia/ati.

---

### Post by NightwishFan on 2010-03-30
Both Xorg.conf linked resulted in a broken xorg which we had to remove the xorg.conf to fix. Would just adding the section about the screen and making the res higher work? I am quite sure I tried that and it had no effect. Is there really no way for this to work?

I know it is old unsupported hardware but it has to be possible. I am not the mega-hacker to make it happen though which is why I posted here.

---

### Post by QIII on 2010-03-30
This is OpenSUSE, but you may be able to pick and choose:

[http://forums.opensuse.org/archives/sls-archives/archives-linux-tweaks/archives-sample-config-files/382301-xorg-conf-via-km400.html](http://forums.opensuse.org/archives/sls-archives/archives-linux-tweaks/archives-sample-config-files/382301-xorg-conf-via-km400.html)

This is a fairly old bug on launchpad, but it has some recent entries ... and a solution that has apparently worked:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-vesa/+bug/258764](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-vesa/+bug/258764)

---

### Post by NightwishFan on 2010-03-30
The OpenSUSE one is deprecated as it mentions the "via" driver. Ubuntu uses the "OpenChrome" one.

I will try using the xorg.conf mentioned in the Ubuntu bug report.

---

### Post by NightwishFan on 2010-03-30
Sorry for double post.

The Xorg.conf listed at the bottom of this page worked.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-vesa/+bug/258764](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-vesa/+bug/258764)

Thanks QIII and others!

---

