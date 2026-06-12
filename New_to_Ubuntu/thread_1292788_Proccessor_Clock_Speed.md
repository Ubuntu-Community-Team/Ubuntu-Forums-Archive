---
title: "Proccessor Clock Speed?"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by Niko Johnson on 2009-10-16
im currently using a celeron proccessor with a 1.8 GHZ of power. but i think i want a little bit more out of it. does anyone know how to over clock a proccessor in ubuntu. do you think it is wise to over clock a celeron? i dont really have any problems with it and its not slow.. i know dont fix it if its not broken but i would like to know how to set the clock speed in ubuntu anyway, even if i dont do it myself.

---

### Post by falconindy on 2009-10-16
Overclocking is done at the BIOS level, not the OS level.

---

### Post by LowSky on 2009-10-16
The easiest way to overclock is to increase multiplier to the Front Side Bus (FSB) from the BIOS.

---

### Post by CharlesA on 2009-10-16
> **falconindy said:**
> Overclocking is done at the BIOS level, not the OS level.

> **LowSky said:**
> The easiest way to overclock is to increase multiplier to the Front Side Bus (FSB) from the BIOS.

Both of these. I think there are OC utilities for Windows, but I don't know if those exist for Linux.

But as a general rule-of-thumb, any OC you do is done in the BIOS.

---

### Post by Niko Johnson on 2009-10-16
Right on.. thanks for the quick replys.. how do i go amongst doing it in the bios? would you recommmend it? i dont want to regret it later if i mess up my system

---

### Post by CharlesA on 2009-10-16
It depends on the BIOS. I know on mine I had a "softmenu" to overclock the CPU.

---

### Post by Niko Johnson on 2009-10-16
alright sounds good. ill check it out

---

### Post by XCan on 2009-10-16
If you have a branded computer it gets harder. But regardless, the preferred way to overclock is through BIOS even if you can do it through softwares. Besides, not all mobos supports overclocking using a software. Some high-end mobos come with softwares from the producer, however, those, as we know are bloated. AMD has a general software as well that works with some chipsets. But so far, I have only seen reviews stating it to be buggy and worse than doing it through BIOS.

---

### Post by ajgreeny on 2009-10-16
I did run my amd sempron 2400+, which has a clock speed of 1670MHz, at 2000MHz for a while, but then found that the regular fsck that is scheduled every 80 boots on my machine (30 by default, I think) locked up and could not continue, so I changed the clock speed back.  I didn't see much difference in speed, but it could be worth trying.

PS:  I did it in the BIOS, as most people have suggested.  It's dead easy to do, but read the warnings about it in BIOS, if any appear, and be prepared to go back to normal if the system becomes unstable.

---

### Post by wnderinguy34 on 2009-10-16
> **Niko Johnson said:**
> Right on.. thanks for the quick replys.. how do i go amongst doing it in the bios? would you recommmend it? i dont want to regret it later if i mess up my system


If its an OEM system like HP/Dell/Acer etc... there may not be any settings available in the BIOS to enable you to OC.If you know the make/model of the Motherboard or even the Computer make/model it would be helpful.

---

### Post by lavinog on 2009-10-16
How much memory do you have?
You might get a bigger performance gain by adding memory.

---

