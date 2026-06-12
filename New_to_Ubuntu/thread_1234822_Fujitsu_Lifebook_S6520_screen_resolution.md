---
title: "Fujitsu Lifebook S6520 screen resolution"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by grj23 on 2009-08-08
Hi All

I've just got a Fujitsu S6520, and immediately upgraded it from the operating system it came with to Ubuntu 9.04.  What a pleasure!  Thanks everyone.  I had a printer and screen extras and they both worked effortlessly.  More than I'd wanted really.  The extra screen acts as my main screen when I'm at the office, but the laptop screen continues to be a little bit of extra screen real-estate seamlessly connected to the main one.  But I digress.

One of the things on the laptop screen though, is that all of the space is not used.  There's a black gap on either side of the usable screen.  It seems (from the reading I've done) that the resolution is meant to be 1280x768, but that doesn't seems to be an option.  I'm using 1024x768, and suppose that this is where the sticking point is.  But how to change?  I read some stuff about openchrome, but then read that this is included or not necessary for Ubuntu 9.04.  

My xorg.conf is:
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2048 768
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

I (cunningly) thought to change the 2048 to 2560, but alas.  

I also so some advice on [http://hp2133linux.blogspot.com/2009/03/installing-ubuntu-904-beta.html](http://hp2133linux.blogspot.com/2009/03/installing-ubuntu-904-beta.html)
saying to change xorg.conf to this
Section "Device"
Identifier "Configured Video Device"
Option "PanelSize" "1024x600"
EndSection

I did this, making the obvious substitution, but again alas.

Any help appreciated

G

---

### Post by rednano12 on 2009-08-08
System -> Preferences -> Screen Resolution.

Enjoy!

---

### Post by grj23 on 2009-08-10
> **rednano12 said:**
> System -> Preferences -> Screen Resolution.

Enjoy!

:lolflag:

Thanks for that.  I should obviously have mentioned that I did go to System->Preferences->Display (there is no screen resolution, perhaps a change from Ubuntu 8?), and tried to change the resolution there, but the only available options were 1024x768, and lower resolution multiples of that.  At the lowest resolutions there were some slightly different aspect ratios, eg 720x400.  It seems  pretty clear that it thinks I've got a 4:3 aspect ratio...

G

---

### Post by grj23 on 2009-08-10
Okay, so this is interesting.  I restored my xorg.conf to its original state, and then added the Option "PanelSize" "1280x768" line, which enabled me to select the new resolution from the System-Preferences-Display, which then filled up my screen beautifully (after a restart).  

So it seems that the external monitor installation must have fiddled with the xorg.conf.  Interesting.  Will have to see how that all works tomorrow when I plug it in again...

Thanks for all help

G

(xorg.conf is below)

Section "Device"
	Identifier	"Configured Video Device"
	Option "PanelSize" "1280x768"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by grj23 on 2009-08-12
Hi All

So everything works fine now.  When plugging in the second monitor (and unchecking mirror) it asks to make a change, but this works pretty well.  My xorg.conf is:
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2304 1061
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option "PanelSize" "1280x768"
EndSection


after the automatic updates from my previous post.

---

