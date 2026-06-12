---
title: "Brightness problem in 10.04"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by newbie2010 on 2010-08-08
HI, 

I have installed Ubuntu 10.04, in my HP8530W laptop. The display brightness on my screen, is very less. I have tried increasing brightness, from the power manager, where it shows 100%. Functional keys doesn't work...Please help me! 

Details of my laptop can be found here

[http://www.linlap.com/wiki/hp+elitebook+8530w](http://www.linlap.com/wiki/hp+elitebook+8530w)

Thanks in advance! Looking forward for a reply soon!

---

### Post by yetiman64 on 2010-08-08
I'm not sure if this will make much difference, but there is a note about your graphics driver on the site linked,

> need 177.80 or newer nvidia binary driverYou could check what driver is in use by going to System > Administration > Hardware Drivers and see which driver is in use (if any) and maybe try enabling the NVidia proprietary drivers if they are not already in use. 

I think the "NVidia current" drivers are at 195.xx, if they are listed as available for you.

Edit: also note from the link,
>    - For Backlight-Control with fn-F9/fnF10: &#8220;gksudo gedit  /usr/share/hal/fdi/information/10freedesktop/10-laptop-panel-hardware.fdi&#8221;  add 8530w befor 4410s in line 27. Reboot. Now the keys are working  fine!


  this may help in getting the lighting function keys to work better.

---

### Post by newbie2010 on 2010-08-08
Perfect!!! I changed my driver from NVIDIA 173 to current version and also, find my function key to be now working!!! Thank you for the prompt response! :)

---

### Post by yetiman64 on 2010-08-08
Your welcome newbie2010,
If all continues to work ok for you, could you please mark the thread as solved? Link #5 in my sig has instructions on how to do that. Cheers from yetiman64.

---

### Post by newbie2010 on 2010-08-08
Sure! Sorry for the slight delay though! :)

---

