---
title: "Ubuntu is running in low-graphics mode"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by bkadoctaj2 on 2009-08-17
Hi everyone,

I'm sorry to ask for help on my first post here, but I just installed Ubuntu 9.04 on my desktop alongside Windows XP, Windows 2000, and openSUSE 11.1.  The first time I logged into Ubuntu, I was given the option automatically to install the best nVIDIA driver for my display, but after doing so and rebooting, I found that my screen resolution was stuck at a horrendous 800x600.  I was luckily (lol) given the option of using an even lower resolution though.

Anyway, I searched the Net for people with similar problems and how they resolved them, trying to be as hands-on as I could.  I tried editing my /etc/X11/xorg.conf file but when I rebooted I got the following message:

```
Ubuntu is running in low-graphics mode

The following error was encountered.  You may need to update your configuration to solve this.

(EE) Unable to find a valid framebuffer device
(EE) NV(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
(EE) Screen(s) found, but none have a usable configuration
```

After uninstalling the nVidia drivers I downloaded, I rebooted but am still left with the same message above.  When I click [OK] I am forced to "Run Ubuntu in low-graphics mode for just one session" as "Reconfigure graphics" doesn't take care of anything.

My monitor is a digital TV/monitor that is probably not too well known called the APEX LD 1919 (19 inch) and my video card is the nVIDIA GeForce FX 5500.

I'm at a total loss for what to do and it's driving me crazy.  I've loved my time using a working Ubuntu desktop, but unless I can fix this I probably will have to leave the OS.  I'd appreciate any assistance greatly.  Thanks in advance and I apologize if I'm too new to the game.

---

### Post by LowSky on 2009-08-17
from terminal run

sudo nvidia-settings

it will open the Nvidia gpu setting s window fomrthere you can set the correct resolution, dont forget to save to X

---

### Post by bkadoctaj2 on 2009-08-17
> **LowSky said:**
> from terminal run

sudo nvidia-settings

it will open the Nvidia gpu setting s window fomrthere you can set the correct resolution, dont forget to save to X

First off, thank you for a speedy response.

Second, I think I'd first have to reinstall the nVIDIA drivers, but after I do, I have a feeling I'm going to get the same limitations I had before.  I was given a choice between two really low resolutions (I can't remember exactly which but they were only as high as 800x600 max) and auto, which was the highest of those two.

I'll give it a try and let you know what happens.

---

### Post by bkadoctaj2 on 2009-08-17
Okay, so now that I have installed the recommended nVIDIA drivers with the assistance of envyng, my display begins with a resolution of 640x480...  it's so bad that even the word "System" in the top panel is cut off...

I used the Terminal to type "sudo nvidia-settings" but just as before, I am left with the following three options for Resolution: "auto", "640x480", and "320x240".

What do I do?  :(

EDIT:  Well, I don't know what the **** the deal is, but I manually edited the /etc/X11/xorg.conf file in the following manner:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bkp
sudo gedit /etc/X11/xorg.conf
```

Deleted

```
Section "Device"
Identifier	"Configured Video Device"
EndSection
```

And edited Section "Screen" like this:

```
Section "Screen"
Identifier	"Default Screen"
Monitor		"Configured Monitor"
Device		"Configured Video Device"
DefaultDepth	24
SubSection "Display"
Modes		"1440x900"
EndSubSection
EndSection
```

Then I rebooted and I was able to boot right into Ubuntu without a warning about low-graphics mode.  The screen was offset about 1/2 inches to the right but after using envyng to remove the nVIDIA driver I had installed and rebooting, everything appears to be fixed.  I can't adjust my screen resolution from within the GUI, but it's not a problem at this point.

---

### Post by fourbit on 2009-08-19
I have been fighting a problem like this for a week or so and I removed the Device section like you did. That worked with the same problem with the screen moved to the right. Now, I don't understand your statement "after using envyng to remove the nVIDIA driver" . What did you use to remove the driver?

Thanks,
Paul

---

