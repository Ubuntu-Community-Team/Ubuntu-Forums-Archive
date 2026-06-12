---
title: "how can I make my screen dimmer with intel integrated graphics and the newest ubuntu?"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by foolguy on 2010-06-26
Hi, the screen dimming slider does not work for my laptop, but I was able to do it when I ran windows on this machine. Does anyone know how to make this work? I have installed "monitor settings" but that does not seem to work, and the only other fix I have been able to find is for nvidia graphics cards.

I can use terminal a little bit, but other than that I am a Linux noob. If anyone knows how to fix this that would be great!

Thanks,
Foolguy

---

### Post by mikewhatever on 2010-06-26
Laptops usually have dedicated keys for adjusting brightness. Do they work?

---

### Post by roger_1960 on 2010-06-26
Hi

You could right click on the panel (bar at top or bottom) and select Add to panel and then install the "Brightness Applet"  This works OK but does not allow the brightness to be turned right off (at least not on my Toshiba A200) The Fn keys do not work on this laptop for any of the vol, brightness etc controls but there are ways around it!

---

### Post by Stigmata13 on 2010-06-26
If you are using an older Intel chipset, you may be out of luck. From personal experience I've found Ubuntu (or just Linux in general, I guess) support for these chipsets to be pretty bad. But if you have fn keys you can try that, and if that doesn't work try right clicking one of your panels and selecting "Add to Panel.." and choosing the brightness applet, and changing it from there.

---

### Post by foolguy on 2010-06-26
> **Stigmata13 said:**
> If you are using an older Intel chipset, you may be out of luck. From personal experience I've found Ubuntu (or just Linux in general, I guess) support for these chipsets to be pretty bad. But if you have fn keys you can try that, and if that doesn't work try right clicking one of your panels and selecting "Add to Panel.." and choosing the brightness applet, and changing it from there.
I think I may just be out of luck. I have the brightness applet, and the fn keys control the slider on said applet, but the slider is for show and doesn't actually do anything.

Oh well, thanks anyways.

---

### Post by bjornsol on 2010-06-26
Thanks, the brightness applet helped.  However, the Fn-F9/F10/F11 keys on my laptop (HP EliteBook 8530p) used to work fine for adjusting the brightness on Ubuntu 9.10 and 9.04, but not in 10.04.  They still work fine in Windows.  What happened in 10.04 to break that functionality, I wonder?

Thanks,

Bjorn.

---

### Post by calmsiva on 2010-06-28
sir,

a partial solution is L

System  -> Preferences  ->  Power Management

- in this you can set the "Set Display Brightness" both in AC and Battery Mode (cannot do it seperately for each one).  

- more importantly after setting - click "Make Default".

Hope this gives you some reprieve.:popcorn:

---

