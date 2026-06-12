---
title: "Custom resolution?"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by JamesParnell on 2009-10-28
h ave a problem with my screen, some windows overhang..i have make several threads about it and many people have tried to help, but none of these suggestions have worked....


Now i think i need to increase my screen resolution from 1024x600 to 1024x7/8/900,

can someone give me a detailed guide on how to accomplish this..



Thanks.

---

### Post by JamesParnell on 2009-10-28
bump

---

### Post by Bölvaður on 2009-10-28
dont bump!!!!

wait a whole day before bumping your threads, not 25 minutes.



this should help you


**/etc/X11/xorg.conf**
```
Section "Screen"

# Removed Option "metamodes" "1280x1024_75 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x1024_75 +0+0; 1280x1024 +0+0; 1280x960 +0+0; 1152x864 +0+0; 1024x768 +0+0; 800x600 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
```



this is the part of the file where you can set custom resolution.
you havent provided any details about anything so I cannot help you any further. I think google will help you a LOT with what you need to change in your xorg.conf

---

### Post by JamesParnell on 2009-10-28
what details would you need???


i have a samsung nc10 netbook with a 11" screen. i dunno what i can say.

---

### Post by Bölvaður on 2009-10-28
I googled "xorg.conf resolution" and this is the first thing that came up. My patience have been lowered by the bump by great margins so I will just stick to "seek and you will discover". Otherwise I would have probably welcomed the question with a similar face as I have in my avatar.

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by JamesParnell on 2009-10-28
[PHP]
Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"

EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"


EndSection[/PHP]

what would i edit, and how..i have looked at the site in the above post but it did not help as the examples are nothing like my xorg.conf...all i want is a 19:9 ratio screen, bigger than 1024:600..


I need to find a way to edit this as my windows are really annoying me.

---

### Post by Bölvaður on 2009-10-29
> **JamesParnell said:**
> 
**Section "Screen"**
    **Identifier**    "Default Screen"
   ** Monitor**        "Configured Monitor"
    **Device **       "Configured Video Device"


EndSection


From the link you looked at.
```
**Section "Screen"**
    **Identifier    "Default Screen"**
    **Device**        "NVIDIA Corporation NV34 [GeForce FX 5200]"
    **Monitor**        "CM752ET"
    DefaultDepth    16
   [SIZE="5"] SubSection "Display"
        Depth        16
        Modes      "1024x768_75.00"
    EndSubSection[/SIZE]
EndSection
```

(the bold letters are the stuff that are in common, the big letters are the words you are supposed to implement)

change Modes to what ever comes to your mind. And note that this is (well this looks like to me)

Xpixels×Ypixels_FPS

that is first comes resolution with x between the X and Y values and then _ followed by the refresh rate of the monitor.


it looks like you dont have a proper driver enabled... I would assume that is weird.
:( it's cloudy today :(

---

### Post by Wim Sturkenboom on 2009-10-29
Next time, please give references to the threads that you already had opened for the subject so we do not give the same advice. Please do so in your next reply.

The spec of your netbook states 1024x600 ( [http://www.samsung.com/za/consumer/detail/spec.do?group=computersperipherals&type=notebookpc&subtype=nseries&model_cd=NP-NC10-KA01ZA](http://www.samsung.com/za/consumer/detail/spec.do?group=computersperipherals&type=notebookpc&subtype=nseries&model_cd=NP-NC10-KA01ZA) ) so I don't give you much chance. The *'monitor' hardware* is designed for that resolution.

A higher vertical resolution (more lines) implies less time for a line to be written from left to right (assuming vertical refresh rate stays the same) and therefore a higher horizontal frequency and it's more than likely not designed for that. What is the current vertical refresh rate?

Except for that, it will not look too great because one pixel will now have to display the information of a mix of 2 pixels vertical (if you increase to 900; actually of 1.5 pixel). And circles will not look like circles anymore but like ovals.

Are you using Ubuntu Netbox Remix? Version?

---

