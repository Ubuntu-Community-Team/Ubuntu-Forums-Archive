---
title: "Resolution Problems"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by KakDela on 2009-07-30
I've looked through the forums but cant find an answer. My native resolution is 1024x800, but the only two options in system>preferences>display are 800x600 and an even lower one. I'm using 800x600 now, but as you can imagine, it looks horrible. Any help?

I am running Ubuntu with Gnome using wubi (I ran it before from a live USB, and had the same problem, I dont intend to try to dual boot until it works on wubi).

My xorg.conf file doesn't have any of the usual settings: after the comments, all it says is > 
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
My video card, as given by
 lspci | grep VGA
is 
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)

btw, I am a newbie at Linux, so any help should be step-by-step. Thanks!

another note: when I was booting off of a live USB, at one point I logged out, and back in again, and found the resolution to be perfect. However, it reverted back to 800x600 next time I rebooted, and I haven't been able to recreate the effect since.

---

### Post by Vakman on 2009-07-30
Follow this [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)
It will show you how to manually edit Xorg file and add the resolution you want. Assuming your drivers are installed correctly. If they are then you should probably have 3D supported so also post the output of ```
glxinfo | grep direct
```

---

### Post by KakDela on 2009-07-31
oh, nvm, I solved the problem by installing one of the drivers in system>hardware drivers

i'd tried to do that before, but on my live usb it wouldn't work because all settings were erased when I tried to reboot to enable the drivers.

Thanks anyway.

---

### Post by Vakman on 2009-08-01
> **Thisislaw said:**
> Assuming your drivers are installed correctly.[/CODE]
> **KakDela said:**
> oh, nvm, I solved the problem by installing one of the drivers in system>hardware drivers
i'd tried to do that before, but on my live usb it wouldn't work because all settings were erased when I tried to reboot to enable the drivers.
Thanks anyway.
Yeah, I had assumed that you had already installed the proper drivers. Sorry.

---

### Post by Brutus2006 on 2009-08-01
This is what I found to work for me I had the same problem before.
Although I have a Nvidia card. 

First I made sure I had all essential drivers. Although Im not sure if this was the problem it seems to be the monitor.

Then open up two terminal windows.
In the first open the xorg file for editing, and find the monitor section

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf

In the second, for a resoultion/refresh rate of (ex. 1280x1024@60mhz) type:

gtf 1280 1024 60

This will give you the Modeline, you need so cut and paste into the monitor section of the xorg file.

Example

Section "Monitor"
	Identifier	"Configured Monitor"
	Option "DPMS"
	HorizSync 28-64
	VertRefresh 43-60
	# 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
  Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync


Change the HorizSync and VertRefresh to what is in your manual. Also you can optionally change the identifier to what ever you wnat it to say. The device and monitor in the screen section have to match the identifier.

Must do a full shutdown not a restart and it should work.

Like I said before I dont think it has much to do with you video card but more your monitor. 

Goodluck

---

