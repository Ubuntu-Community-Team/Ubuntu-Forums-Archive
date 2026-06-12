---
title: "screen resolution problems still"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by scrimple101 on 2009-11-05
I am still having problems with my screen resolution in Ubuntu 9.10. I have a Nvidia GForce FX5100 graphics card. The highest resolution i can get is 640x480 pixels after downloading the Nvidia driver. 

This is the contents of xorg.conf file: 

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

That is all there is in the file. Does anyone know what's going on know how i can fix this resolution problem?
All the best, Rob.

---

### Post by ukripper on 2009-11-05
Did you install nv driver via System>Administration>Hardware Drivers?

---

### Post by scrimple101 on 2009-11-05
> **ukripper said:**
> Did you install nv driver via System>Administration>Hardware Drivers?

Yes i did.
Rob

---

### Post by ukripper on 2009-11-06
If you go to  **Administration-->Nvidia X Server Settings** can you see your card displayed there?

---

### Post by scrimple101 on 2009-11-06
> **ukripper said:**
> If you go to  **Administration-->Nvidia X Server Settings** can you see your card displayed there?

Yeah i can see the card there but it still doesn't help me because i still can't change the resolution to 1024 * 768

---

### Post by ukripper on 2009-11-06
edit

Sorry got on the wrong end of the stick so deleted this post.

---

### Post by scrimple101 on 2009-11-06
> **ukripper said:**
> Does you screen supports more than 1024 * 768 resolution?

i don't know but i know it does support 1024 * 768

---

### Post by ukripper on 2009-11-06
sorry wrong analysis. Hence, post deleted

---

### Post by Teber on 2009-11-06
> **scrimple101 said:**
> Yeah i can see the card there but it still doesn't help me because i still can't change the resolution to 1024 * 768

i'm sorry ukripper. the OP would seem to want to set screen res to 1024*768?

---

### Post by ukripper on 2009-11-06
> **Teber said:**
> i'm sorry ukripper. the OP would seem to want to set screen res to 1024*768?

Thanks for pointing out mate. It has been long nite for me..mind was elsewhere...My apology to OP..

---

### Post by ukripper on 2009-11-06
Can you boot into your ubuntu livecd and see if you get resolution you want?

---

### Post by scrimple101 on 2009-11-07
> **ukripper said:**
> Can you boot into your ubuntu livecd and see if you get resolution you want?

No when i boot with the live CD the highest resolution i can get is 800 * 600

---

### Post by anujv73 on 2009-11-07
hey hi i am even get the same problem with Ubuntu 9.04 i am just geting  resolution 640x480 and 800x600 i am wetting for reply too

---

### Post by scrimple101 on 2009-11-07
> **anujv73 said:**
> hey hi i am even get the same problem with Ubuntu 9.04 i am just geting  resolution 640x480 and 800x600 i am wetting for reply too

Hello Anujv73, i hope that things get sorted and the resolution problem gets resolved soon. Rob

---

### Post by 8oluf7 on 2009-11-07
I've had this problem and found a solution. Basically, Ubuntu 9.10 doesn't use xorg.conf, so only a minimal file is created. OTOH, if information is put into xorg.conf, it can and will be used. 

**First problem:** 
Option of high resolutions not available. Have you enabled Visual Effects? (System > Preferences > Appearance and click the Visual Effects tab.) If you do this, I think that an extra line appears in your Section "Screen":
```
Option	"AddARGBGLXVisuals"	"True"
```That's the only difference I can see between your xorg.conf and the one I had before I started playing with it. Enabling visual effects also sends the system off to hunt for the appropriate driver! I had a related problem with another machine with an Intel graphics chip - turning off Visual Effects also removed the high resolution options.

**Second Problem:**
In my case I could reset the screen resolution but my choice didn't survive a reboot. The system returned to its default which, with an MX400 card and a LaCie electron22blue monitor, was staggeringly high. If I tried to save the new configuration the nVidia software complained that it couldn't parse the xorg.conf file. There are several descriptions of ways to overcome this problem, but they tend to assume that you have access to the full specification of your monitor - I don't. However, another post in this forum revealed that the way to overcome this roadblock is to rename the xorg.conf file so that the software doesn't find anything and creates a new xorg.conf from scratch, thus doing the 'heavy lifting' for you. So:```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.original
```Then use the nVidia X Server Settings application (System > Administration > NVIDIA X Server Settings) to set the resolution you want. When you've finished, click the 'Save to X Configuration File' button.

Now you can examine the file that's just been created in a text editor, such as gedit. ```
sudo gedit /etc/X11/xorg.conf
```I found a lot of repetition - maybe the previously unsuccessful attempts to modify xorg.conf were stored somewhere and all dumped together! The bits that are important are the "Monitor", "Device" and "Screen" sections. The "Screen" section should contain a line such as:```
Option         "metamodes" "1280x960 +0+0"
```which sets the resolution you selected (in my case 1280x960).

The final step is to combine the essential elements of xorg.conf and xorg.original so that you have an xorg.conf containing the "Monitor" and "Device" sections, followed by a combined "Screen" Section and then the rest of the original file. In my case it looks like this:```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LCA electr22b2"
    HorizSync       30.0 - 121.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce2 MX/MX 400"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1280x960 +0+0"
    Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```The first three lines of the "Screen" section replace the default ```
Identifier    "Default Screen"
```and the ```
Option         "metamodes" "1280x960 +0+0"
```has been inserted.

I hope that helps.

---

### Post by scrimple101 on 2009-11-10
> **8oluf7 said:**
> I've had this problem and found a solution. Basically, Ubuntu 9.10 doesn't use xorg.conf, so only a minimal file is created. OTOH, if information is put into xorg.conf, it can and will be used. 

**First problem:** 
Option of high resolutions not available. Have you enabled Visual Effects? (System > Preferences > Appearance and click the Visual Effects tab.) If you do this, I think that an extra line appears in your Section "Screen":
```
Option	"AddARGBGLXVisuals"	"True"
```That's the only difference I can see between your xorg.conf and the one I had before I started playing with it. Enabling visual effects also sends the system off to hunt for the appropriate driver! I had a related problem with another machine with an Intel graphics chip - turning off Visual Effects also removed the high resolution options.

**Second Problem:**
In my case I could reset the screen resolution but my choice didn't survive a reboot. The system returned to its default which, with an MX400 card and a LaCie electron22blue monitor, was staggeringly high. If I tried to save the new configuration the nVidia software complained that it couldn't parse the xorg.conf file. There are several descriptions of ways to overcome this problem, but they tend to assume that you have access to the full specification of your monitor - I don't. However, another post in this forum revealed that the way to overcome this roadblock is to rename the xorg.conf file so that the software doesn't find anything and creates a new xorg.conf from scratch, thus doing the 'heavy lifting' for you. So:```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.original
```Then use the nVidia X Server Settings application (System > Administration > NVIDIA X Server Settings) to set the resolution you want. When you've finished, click the 'Save to X Configuration File' button.

Now you can examine the file that's just been created in a text editor, such as gedit. ```
sudo gedit /etc/X11/xorg.conf
```I found a lot of repetition - maybe the previously unsuccessful attempts to modify xorg.conf were stored somewhere and all dumped together! The bits that are important are the "Monitor", "Device" and "Screen" sections. The "Screen" section should contain a line such as:```
Option         "metamodes" "1280x960 +0+0"
```which sets the resolution you selected (in my case 1280x960).

The final step is to combine the essential elements of xorg.conf and xorg.original so that you have an xorg.conf containing the "Monitor" and "Device" sections, followed by a combined "Screen" Section and then the rest of the original file. In my case it looks like this:```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LCA electr22b2"
    HorizSync       30.0 - 121.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce2 MX/MX 400"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1280x960 +0+0"
    Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```The first three lines of the "Screen" section replace the default ```
Identifier    "Default Screen"
```and the ```
Option         "metamodes" "1280x960 +0+0"
```has been inserted.

I hope that helps.

Thanks for you help but unfortunately i still couldn't get any different response from Nvidia Setting manager and have decided to use Hardy Heron 8.04 where it is easy to configure the screen with the screens and Graphics section of applications:/usr/share/applications/. I wish it was as easy as this in 9.10.
Regards, Rob.

---

### Post by ukripper on 2009-11-10
> **scrimple101 said:**
> Thanks for you help but unfortunately i still couldn't get any different response from Nvidia Setting manager and have decided to use Hardy Heron 8.04 where it is easy to configure the screen with the screens and Graphics section of applications:/usr/share/applications/. I wish it was as easy as this in 9.10.
Regards, Rob.

Try 9.04 live cd if 9.04 works for you then stick to that. You can even use EXT4 filesystem in 9.04.

---

