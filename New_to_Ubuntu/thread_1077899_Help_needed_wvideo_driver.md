---
title: "Help needed w/video driver"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by yachtpro on 2009-02-22
Hi all,
I am a total linux newbie in need of help. I just built a new system and installed 8.10 on a MSI G31M3 board w/intel G31 chipset. The problem is resolution, I can only get 640x480. In the screen resolution settings under preferences 800x600 is offered but I can't choose it, it always reverts to 640x480. 800x600 would be better but not optimal. Are there any linux drivers for this chipset or will have to install a video card and if so, what is a low budget card that will work. This machine is not going to be used for anything but web surfing and email plus some word processing, and I only need higher resolution so the windows will fit on the screen. Any help is greatly appreciated and many thanks in advance.

---

### Post by mikewhatever on 2009-02-22
Can you post the outputs of the following commands here:
xrandr -q
sudo lshw -C display

---

