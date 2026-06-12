---
title: "Just bought nVidia GeForce 6200, need help as to what drivers I need to get."
date: 2009-01-04
forum: New to Ubuntu
---

### Post by hbah427 on 2009-01-04
I've tried to use Ubuntu's restricted drivers, as well as using nVidia's drivers from their site.

After countless (four) fresh installs of Intrepid and Hardy, I'm almost ready to pull my hair out.

---

### Post by Martin Marshalek on 2009-01-04
Check this post: [http://ubuntuforums.org/showthread.php?t=1002828]("http://ubuntuforums.org/showthread.php?t=1002828")

It will install the current Nvidia beta driver which is 100% better than the drivers under Hardware Drivers

---

### Post by tuxxy on 2009-01-04
Restricted drivers should work fine, what are the issues you have once this driver is activated?

Also you could try envyng to install the correct driver for yuor card, envy is available in the repos.

---

### Post by sbentjies on 2009-01-04
Wow-got me beat. I've only installed one each. Ditched my TNT2 Riva for an nvidia GEForce FX-5200. No further ahead. Is there not a utility to create a custom xorg.conf? I don't have enough hair to pull out.

---

### Post by shad0w_walker on 2009-01-04
Could you describe the actual problem you are having? I gather it's to do with the Nvidia closed source drivers, but that could be anything in a giant list of possible problems. An outline of what happens when you install them would be a great starting point to figure out what's happening.

---

### Post by sbentjies on 2009-01-04
I wish something would work for me. Followed the above steps. Nothing is working. I have a new GEForce FX-5200 card and 8.04 simply will not do more than 800x600. I went through the same hassle with a TNT2 Riva card. I have tried using the Envy drivers, the nvidia beta drivers, you name it. Everything I try to do seems to break X. I even went from 8.10 to 8.04 hoping for better luck. This can only be described as utter frustration. Can somebody please help? I need a coherent solution. Surely there is one.

---

### Post by The Joe on 2009-01-04
sbentjies:

I had the same with my nVidia - the problem is caused by incorrect or non-existent modelines in xorg.conf under "Monitor", you will need the precise modelines for your monitor, luckily with me modelines for a standard CRT monitor worked a treat, but you may not have a standard CRT.

Be careful with whatever modelines you find/use or you may not be able to use higher resolutions, IE: Before I corrected mine I couldn't run anything fullscreen - the monitor turned off.

---

### Post by sbentjies on 2009-01-04
Almost? Good god man, you're patient. I've been going through the same thing and I'm ready to choke  those  responsible for not putting good nvidia support into 8.04 and 8.10 . It's like it was an afterthought, or totally ignored nvidia.  I'm STUCK.

---

### Post by sbentjies on 2009-01-04
I have a GEForce FX 5200 and a Sony (Gateway branded monitor). Every time I have altered xorg.conf, it broke. Damn frustrating. Is there not a way to build a custom file, step by step? Of course now I'm stuck with a blank file because bulletproof X had to strip it out to boot. This has been going on for a month now.

---

### Post by shad0w_walker on 2009-01-04
Have you tried running this? 

```
sudo dpkg-reconfigure xserver-xorg
```

This will give you a series of prompts to build an Xorg.conf file and hopefully will get you a decent resolution. You can then tweak that file to use the nvidia closed driver either manually or using nvidia-xconfig.

---

### Post by sbentjies on 2009-01-04
bulletproof X has allowed me to get back to gnome every time but in the process, strips out my xorg.conf, leaving me with nothing configured-literally. Are these steps going to allow me to re-add this detail?

Thanks,

JP

---

### Post by shad0w_walker on 2009-01-05
It should do, assuming there isn't something else odd going on, it will create a new configuration that should work properly.

---

### Post by wizard10000 on 2009-01-05
> **hbah427 said:**
> I've tried to use Ubuntu's restricted drivers, as well as using nVidia's drivers from their site.

After countless (four) fresh installs of Intrepid and Hardy, I'm almost ready to pull my hair out.

I've got two of them and they've run flawlessly through Gutsy, Hardy and now Intrepid.  On the Intrepid boxes one was a clean install and the other was an upgrade from Hardy.

I prefer to use the restricted drivers in the repos instead of the latest and greatest from nVidia simply because I don't want to reinstall drivers every time a kernel upgrade comes out.

So exactly what happens when you try to use the restricted drivers?

---

### Post by hemicro on 2009-04-28
Had trouble with my 6200 also. Always 800x600 and "unknown" monitor. I modified my xorg.conf file and then ran a hardware driver check which gave me the Nvidia driver version 180 option. I installed it and all works great now. The driver takes a very long time to download/install so be patient. I think the secret was defining the installed monitor functions. Below is the xorg.conf file that works with my computer.


# xorg.conf (X.Org X Window System server configuration file)
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Hyundai"
	Option	"DPMS"
	HorizSync 31-80
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"LCD"
	Monitor		"Hyundai"
	Device		"VIAInt"
	DefaultDepth	24
	#	SubSection "Display"
	#	Depth 8
	#	Modes "1280x1024" "1024x768"
	#	Virtual  1024 768
	#	ViewPort 0 0
	#	EndSubSection
	#	SubSection "Display"
	#		Depth 16
	#		Modes "1280x1024" "1024x768"
	#		ViewPort 0 0
	#		Virtual	800 600
	#	EndSubSection
	SubSection "Display"
		ViewPort 0 0
		Depth 24
		Modes "1024x768" "1280x1024"
		#		Virtual	1024 768
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"VIAInt"
	BusID 	"PCI:1:0:0"
	Option 	"ActiveDevice" "LCD"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	#	Driver "openchrome"
	# Option "LCDDualEdge" "true"
EndSection

---

