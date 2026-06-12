---
title: "Beautiful 1440x900 FINALLY!"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by wolfhabits1 on 2009-09-06
I posted several days ago that I wasn't having any luck with my xorg.conf. I was trying to set the desktop resolution to 1440x900 with the nvidia drivers on my Insignia HDTV which I have been using as my desktop monitor for months at 1440x900 in Windows XP.
Well, after reading the nvidia guide, and an ample amount of trial and error. Success!
I am posting a run-through of how I troubleshot the problem so other linux-newbies might benefit.

I changed three sections in my xorg.config: 
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option "metamodes" "1440x900_60 +0+0" 
    SubSection "Display"
        Depth       24
        Modes "1440x900_60"
    EndSubSection
EndSection

```First I set the 1440x900 resolution, to no avail, the xorg.conf log file read "cannot validate mode." However, I figure it couldn't hurt to not undo the change, and I moved onto my next tweak.
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
Option "UseEDID" "False"
EndSection

```Next,
I read about the "UseEDID" option in the nvidia instalation guide. By changing the option to "false" I disabled the probing for valid modes. Since I was trying to get a HDTV to work as a monitor, and HDTV's don't send EDID information, I figured this might be a good idea.

    ```
 
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 200.0
    VertRefresh     43.0 - 200.0
    Option         "DPMS"
EndSection

```Finally,
I rebooted my computer, but nothing had changed yet. I checked my log, and it still said the mode wasn't valid. So, I decided the xorg.config must be what is inhibiting the high resolusions. While playing around with modelines, I recalled values for vert and horizontal refresh bing triple digits, and I had always wondered why the monitors ranges were set so low in the xorg.conf. My final tweak that set it straight was tuning up the ranges for horizsync and vertsync to 200.

I rebooted my computer, my jaw dropped, and I began to dance in celebration. I had finally achieved 1440x900.

In Sum: check your horizsync and vertrefresh ranges, and consider turning "UseEDID" to "False" if you are trying to get a Television to work as a monitor.
Then, set your dered resolution to your "Metamode" so it will pop up in the desired resolution when you boot up.

Hope this helps someone,
William

(I know the ranges I set for horizsync and vertsunc might be _very_ innapropriate, but they just happened to work. I will be adjusting them very soon. :P)

---

