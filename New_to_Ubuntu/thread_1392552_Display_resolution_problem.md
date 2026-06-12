---
title: "Display resolution problem"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by krmr87 on 2010-01-28
I just installed the latest version of ubuntu and everything is working great, but i just can't set my resolution to anything higher than 800X600.

i also have windows xp on another partition and am able to set the res to 1024x768 which is what i would also like on ubuntu.

does anyone know how to fix this. 
                                                                                                            
                                                                                                                  - thanks Joe

---

### Post by freesitebuilder on 2010-01-28
What video card do you have?

---

### Post by Grenage on 2010-01-28
If installing the proprietary drivers doesn't help (System/Administration/Hardware drivers) then you can take a look at my [guide]("http://www.grenage.com/xorg.html"), to set a custom resolution.

---

### Post by caravel on 2010-01-28
Do you have a CRT monitor?

---

### Post by krmr87 on 2010-01-28
> **freesitebuilder said:**
> What video card do you have?

Intel Corporation 82865G Integrated Graphics Controller



> **caravel said:**
> Do you have a CRT monitor??

yes

---

### Post by caravel on 2010-01-28
I'm not sure about the Intel onboard graphics, but for the CRT you will need a customised xorg.conf with horizontal and vertical frequencies specified.

What is the make and model of the monitor?

---

### Post by krmr87 on 2010-01-28
It's a CTX VL700

---

### Post by Grenage on 2010-01-28
> I'm not sure about the Intel onboard graphics, but for the CRT you will need a customised xorg.conf with horizontal and vertical frequencies specified.

Whether a monitor is CRT or not has nothing to do with it, it's a question of whether the monitor supports EDID, and if that data is correctly received by the graphics adapter.

---

### Post by caravel on 2010-01-28
Googled:

Max Resolution: 1280 x 1024 @60Hz

H Freq: 30-70 KHZ
V Freq: 50-160 HZ

You will need to build an xorg.conf to meet those specs.  I am at work now but I can have a go at this later unless some kind individual can oblige?

---

### Post by caravel on 2010-01-28
> **Grenage said:**
> Whether a monitor is CRT or not has nothing to do with it, it's a question of whether the monitor supports EDID, and if that data is correctly received by the graphics adapter.

I'm fully aware of this, and many older CRTs don't support it.  I know from experience as I had a lot of trouble with my old CRT and Linux.

---

### Post by Grenage on 2010-01-28
I appreciate that, I was quibbling the statement that it was a CRT, therefore manual configuration would be required; that's not true of all CRTs by far.  I know it seems trivial, but it's for the benefit of someone who might read this thread while trouble-shooting.

---

### Post by caravel on 2010-01-28
Fair enough, I should have been more specific, but I think this is quite an old monitor - maybe late 90's or early 00's.  I think it will need the freqs adding to the xorg.conf.

---

### Post by Grenage on 2010-01-28
> Fair enough, I should have been more specific, but I think this is quite an old monitor - maybe late 90's or early 00's. I think it will need the freqs adding to the xorg.conf.

Aye, you're probably right.  As you're at work, I've thrown the following config together;  it should do 1024x769@75:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "CTX"
	ModelName "VL700"
	HorizSync 30 - 70
	VertRefresh 50 - 160
        Modeline "1024x768_75.00"   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "intel"
	VendorName "Intel 82865G"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1024x768"
	EndSubSection
EndSection
```

Modeline probably not required, but it can always be taken out, you can also add more modes.

---

### Post by krmr87 on 2010-01-28
thank you so much guys that worked great :D

---

