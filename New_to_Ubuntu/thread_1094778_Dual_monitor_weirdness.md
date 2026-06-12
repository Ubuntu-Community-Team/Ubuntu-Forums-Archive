---
title: "Dual monitor weirdness"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by Volt9000 on 2009-03-12
Ok I just did a fresh install of Ubuntu on my system, dual booting with Windows XP. I was very pleased to find that everything was working beautifully straight away.

My only problem at the moment is my dual monitor setup. I have a 22" Samsung LCD as my primary and a 17" LG as my secondary. Initially everything was working fine-- Ubuntu detected both monitors correctly and I was able to set their resolutions exactly the way I wanted to.

Then I started tweaking the system. When I went to Preferences > Appearance and tried to enable Normal or Extra video effects, I was told I don't have the proper drivers. Well I remembered earlier Ubuntu complaining about drivers, so I went to Administration > Hardware Drivers. It said it wasn't using any proprietary drivers, but listed a few for Nvidia. I checked on the recommended one (Version 177) and restarted as it requested.

When I got back in, I could enable the Extra video effects, but no longer had dual monitors! :( I checked Screen Resolution and now it only detected one monitor, type Unknown.
What happened? Why did installing video card drivers mess up the monitors?

Here are my xorg.conf files, before and after.

Before (two monitors detected):
> 
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2960 1050
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection


After (one monitor detected):
> 
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Virtual	2960 1050
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


---

### Post by Hospadar on 2009-03-12
The issue is that the nvidia drivers don't present multiple monitors to xrandr (the X11 extension that handles multiple monitors, size, rotation, etc) properly (at least that is my understanding of the issue).

However, nvidia provides a tool to easily configure dual monitors.  if you do Alt-f2 and type in "gksu nvidia-settings" you can configure your dual monitors easily.

Make sure you "save settings to xorg.conf" or whatever they call it.  There's different ways to set up dual monitors, you'll probably want to use "twinview"  I've found it works best with my nvidia cards in the past.

---

### Post by Volt9000 on 2009-03-13
It worked, thanks a million! :D

Oh wait, but now when I log in again the panels appear by default in my secondary monitor, despite the fact that in nvidia-settings I selected my Samsung and checked on "Make this the primary display for the X screen."

I moved the panels over, but is there any way to make this permanent?

---

