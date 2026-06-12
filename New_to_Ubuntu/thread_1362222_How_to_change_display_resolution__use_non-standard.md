---
title: "How to change display resolution / use non-standard resolution"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by sumofchemicals on 2009-12-22
I'm fairly experienced with Windows/Mac but I'm new to Ubuntu. I just installed 9.10 on an IBM Thinkpad T42 (1.7GHz / 512mb / 40GB) and things seem to work fairly well. 

One issue I can't figure out is screen resolution for an external monitor. The display preferences gives me options for 1280x720 and 1024x768, (and lower values I don't care about) but I have a 19" HannsG HW-191DPB with a recommended resolution of 1440x900. Can anyone tell me how to set this up?

I've been reading for a few hours, and saw some people recommend editing xorg.conf. I haven't been able to find the horizontal sync or vertical refresh info for my screen, and it's a little intimidating to make these changes when I'm not really sure what I'm doing. Here's what's currently in my xorg.conf:


```
Section "Screen"
    Identifier    "Configured Screen Device"
    Device    "Configured Video Device"
    SubSection "Display"
        Virtual    2048 768
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection
```Is this what I need to work on? Any other ideas? Thanks in advance for any help!

---

### Post by Raistlin355 on 2009-12-22
So this is the vanilla xorg.conf, your using the default video driver?  You *used* to be able to something like this:
```
Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultDepth 24
        SubSection "Display"
                Viewport  0 0
                Depth     24
                Modes     "1024x768"
        EndSubSection
EndSection

```

However before you try backup the old one, as I have had this go wrong in 9.10.

---

### Post by ST3ALTHPSYCH0 on 2009-12-22
If you have a spare CD or USB stick laying around you could try the link in my sig. Mileage may vary.

---

### Post by Raistlin355 on 2009-12-23
Hey ST3ALTHPSYCH0, I was looking for that thread, I was gonna link it for op, thanks for doing my light work!!

---

### Post by sumofchemicals on 2009-12-23
Thanks for your help all. I didn't realize right away that the sound isn't working either. Since it's a fresh install I'm thinking I might just change to 8.04 or at least an earlier version and see if that makes things better.

---

### Post by ST3ALTHPSYCH0 on 2009-12-23
Not at all, it was my thread. The devs took a powerful tool from us. I'm really just trying to create enough stink to get it back. LOL

I found 9.o4 to be a pretty solid release. At very least, make sure to enable the backports in the update manager so you can get the newest software.

---

