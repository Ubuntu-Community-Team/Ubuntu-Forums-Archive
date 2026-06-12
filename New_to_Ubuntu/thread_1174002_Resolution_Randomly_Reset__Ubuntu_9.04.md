---
title: "Resolution Randomly Reset  Ubuntu 9.04"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by LAKOSWOLF on 2009-05-30
Greetings all,

So far I haven't had any major issues using Ubuntu, but recently as of yesterday when I started up my PC the resolution in Gnome and GDM was 1024x768 I had previously set it higher than this something just above 1280x1024 although for some reason I can't recall the exact resolution. This has not happened before, so I am a bit baffled. I attempted to set the resolution higher but Nvidia X Server Settings only gives me 1024x768 or less. I have not changed anything in terms of my display configuration recently, perhaps this was caused by an update of some kind? Needless to say I googled the issues and reset my Xorg file a number of times but to no avail. I also tried reinstalling the Nvidia driver with no luck.

This is my current Xorg.conf
> 

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection



Suggestions and solutions would be greatly appreciated, this 1024x768 stuff is driving me crazy.

Thanks,

-Lakoswolf

---

### Post by Gone fishing on 2009-05-30
By default the nvidia-settings runs as a normal user and its setting are lost on reboot (I find this handy as I use it to turn on twinview when I need it).

However, if you Alt F2 and paste ```
gksu nvidia-setting
```s then put you password in the dialog box make the changes and then click "Save to X configuration file" it will save the settings.

---

### Post by Gone fishing on 2009-05-30
Sorry I read too fast but I'd install the nvidia drivers then set the resolution you want with nvidia-settings as root (gksu). I have had a problem with weird resolutions when the monitor wasn't fully plugged into the vga slot. An never got the proper resolution without the nvidia driver

---

### Post by LAKOSWOLF on 2009-05-30
> **Gone fishing said:**
> Sorry I read too fast but I'd install the nvidia drivers then set the resolution you want with nvidia-settings as root (gksu). I have had a problem with weird resolutions when the monitor wasn't fully plugged into the vga slot. An never got the proper resolution without the nvidia driver

Thanks for the suggestion, but no luck. I know both the monitor and card are capable of 1280x1024 however, is there a way I can manually set it to that particular resolution?

---

### Post by Gone fishing on 2009-05-31
Start up in recovery mode then go to the option to reconfigure the X server?

---

### Post by LAKOSWOLF on 2009-05-31
> **Gone fishing said:**
> Start up in recovery mode then go to the option to reconfigure the X server?

Tried before as well, although I forgot to mention that earlier. No such luck there either, reset me to defaults but didn't give me the missing resolutions.

---

