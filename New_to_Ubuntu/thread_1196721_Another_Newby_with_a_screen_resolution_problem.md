---
title: "Another Newby with a screen resolution problem"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by ishmael2k on 2009-06-25
OK,

I am starting up with Ubuntu again after a couple years off. I installed 9.04 with no problems, but have yet to be able to set my screen resolution or my refresh rate. I have a Geforce 5200 and am running an IBM P76 monitor. Installed the proprietary drivers for the card but they (Either set) won't let me change anything. Right now the screen is at 800x600 and 60HZ 

I need to get it up to at least 75HZ and 1024x768 for it to be usable. 

I have searched the forums and tried some of the helps but no luck yet. 

My linux level of knowledge is low but I want to kick the MS habit badly.

Help!

Rob

> Did you install the proprietary drivers through the "hardware drivers" dialogue 

Yes, sorry about the initial lack of info.

First driver ver. 173.14.16 Recommended
Second driver ver. 96.... 


Here are my terminal readings for both drivers 

tyr@tyr-desktop:~$ glxinfo | grep server
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
tyr@tyr-desktop:~$

> Click X Server Display Configuration and then put resolution to what ever you want. Remember to save the change by clicking Save to X configuration file (that is xorg.conf)
Is it stuck at low resolution?

Yes, with the first driver it is stuck at 640x480 and with the second it is stuck at 800x600.

> then you might need to edit the file xorg.conf (/etc/X11/xorg.conf) manually.

I am going to try this now. (Once I figure out how to...)

Thanks for the help!

---

### Post by adam_kimber on 2009-06-25
Did you install the proprietary drivers through the "hardware drivers" dialogue or via something like Envy?

---

### Post by Bölvaður on 2009-06-25
putting newby in your title will not draw people to it as then you might not understand the solutions you are given and the person giving them might just give up.


If it works, find the "edit tags" on bottom of the thread while you read it (above quick reply)

Press: Alt+F2
Type: gksu nvidia-settings
Click X Server Display Configuration and then put resolution to what ever you want. Remember to save the change by clicking Save to X configuration file (that is xorg.conf)
Is it stuck at low resolution? then you might need to edit the file xorg.conf (/etc/X11/xorg.conf) manually.

If there is no nvidia-settings program on your computer then you might not have the driver installed.
Check it by opening the terminal (applications &#8594; accessories &#8594; terminal) and copy and paste ```
glxinfo | grep server
```
you paste it with either ctrl+shift+v or right click and paste with mouse.

now, report on your status and what you did.

---

### Post by ishmael2k on 2009-06-25
Ok I updated the first reply, now here is the second update. 

I edited the xorg.conf file to no avail. 

Here is the file: 

# xorg.conf (X.Org X Window System server configuration file)

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


I added the following lines:
	HorizSync       60-90
        VertRefresh     50-100

I inserted these below the 
Section "Monitor"
	Identifier	"Configured Monitor"

When I re-booted Ubuntu went into the low res graphics mode and allowed me to re-edit the file. So I am back at square one...

Any suggestions?

---

### Post by adam_kimber on 2009-06-25
Erk! You are running Jaunty, so xorg automagically detects your best settings these days. Sometimes it gets it wrong. Most settings are not in the xorg.conf file. I believe it jsut performs overrides now not defaults. 

HAve you tried the nvidia control panel? nvidia-settings should do the trick.

---

### Post by ishmael2k on 2009-06-25
Thanks for the quick reply.

Yes I tried through the Nvidia controls but it was locked there also.

BUT!! I found a solution!! It turns out that I had inserted the edit in the wrong place the first time. I re-did it and am no working at 1024x768 85HZ which is about ideal for this monitor. 

Thanks again for the help!

Now on to more fun stuff with it.

Rob:popcorn:

---

### Post by ishmael2k on 2009-06-25
As stated in the previous reply I got it to work at 1024x768 85hz which was good but I then went in and did some more looking and by opening up the resolutions I am now able to go all the way up to 1900x1440 @ 60=HZ !! 

Needless to say on a 17" monitor that would be absurd. I am happily running 1280x1024 @ 75hz.

I am already making plans to back up my data on my W2k box and switching it over to 9.04

---

