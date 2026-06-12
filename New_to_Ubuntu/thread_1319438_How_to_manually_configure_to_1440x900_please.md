---
title: "How to manually configure to 1440x900 please"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by LanceyD on 2009-11-08
I i want to set my monitor to its proper resolution but option is for 1024x768.

If there is one thing that Ubuntu needs to fix it's forcing resolutions, this is the 2nd install i'm having problems with now :(

I've tried from what ive learnt previously but no success yet.  Want to set it 1440x900

```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
Modeline "1440x900_56.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Option "metamodes" "1440x900_56 +0+0"
EndSection
```

---

### Post by LanceyD on 2009-11-08
ok, now it's on terminal only.  i have tried to restore from backup, but backup does not exist, i'm sure i made one.  i cannot edit the xorg.conf from terminal "cannot start display" or something.

how can i now fix this?

ive spent hours just to change screen resolution, should be simple :(

---

### Post by LanceyD on 2009-11-08
please someone, all those big throbbing brains someone can help :(

---

### Post by LanceyD on 2009-11-08
Ive used the "sudo nano" command to remove the lines from xorg.cong that caused the problem and i can now starts xserver.  

But i still cannot get it to work in 1440x900.  Its running at 1024*768 on a widescreen 16x9 screen, so everything is fat :p all options in display properties is for 4x3

Monitor is a Mirai DML-419W210

---

### Post by CharlesA on 2009-11-08
Ensure the correct video drivers are installed.

---

### Post by LanceyD on 2009-11-08
How do i find out?  Its just a generic onboard thing.

I thought you need to modify the xorg.conf file if the monitor is not detected properly, which is the problem i have but i don't seem to be able to modify it correctly.

---

### Post by HotShotDJ on 2009-11-08
> **LanceyD said:**
> How do i find out?  Its just a generic onboard thing.

I thought you need to modify the xorg.conf file if the monitor is not detected properly, which is the problem i have but i don't seem to be able to modify it correctly.First of all, what version of Ubuntu are you running.  Secondly, we need to know what graphics adapter is installed in your computer.  You can get that by running the following code in a terminal:```
lspci | grep VGA
```It will be much easier for us to help you if we have that information.

---

### Post by LanceyD on 2009-11-08
Thanks its Ubuntu 9.10, but will have to wait until i go round to this chaps house again.  I was introducing him to Ubuntu, but he was most miffed that the screen was in fat mode, didn't make a good impression on him that there are problems right from the beginning :p 

I don't know why it's so complicated to change.

The only modes presented were all 4:3 and up to 1024x768, no widescreen modes at all.

---

### Post by CharlesA on 2009-11-08
Probably cuz it's not using the right driver for the video card.

---

### Post by LanceyD on 2009-11-08
When i encountered the same problem with my computer it was because it didn't detect the monitor.  

In this institance it seems the same problem, "unknown monitor" in the display properties.  I did try and find out what graphics driver its using but that wasn't easy either.  If you don't know the terminal commands then it's quite a difficult operating system to use other than the basics presented.  

There was no indication of any problems during installation.

It's so frustrating, why oh why can you not force the resolution and refresh that you want.

Oh well.

---

