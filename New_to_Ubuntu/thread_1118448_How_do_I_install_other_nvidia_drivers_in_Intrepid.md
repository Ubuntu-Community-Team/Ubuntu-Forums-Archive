---
title: "How do I install other nvidia drivers in Intrepid?"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by diablo75 on 2009-04-07
Currently (according to the Hardware Drivers manager app in the system menu) I have available to me versions 173 and 96 for my nvidia video card.  However, I have noticed (on more than one PC) that for some reason, 173 is causing some strange glitching very recently that is for the time being averted by disabling the drivers.  But I have found on one PC that had the 177 drivers available in the Hardware Drivers manager that using 177 instead of 173 seemed to fix the problem, and I'd like to install these drivers on another machine that doesn't currently list them.

How do I install the 177 drivers (or others)?

---

### Post by Temposs on 2009-04-07
It sounds like your graphics card doesn't support the 177 drivers. Generally, the drivers listed under Hardware Drivers are the ones that support your graphics card. If it's not listed there, it probably won't work properly.

---

### Post by MockY on 2009-04-07
You could always try out the latests drivers from Nvidia's website [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Download the drivers for you card, go to tty2 (Ctrl+Alt+F2), type ```
sudo killall gdm
``` and then ```
sudo sh ./driver.file.run
```

---

### Post by zeex on 2009-04-07
I don't understand what do you mean by other nvidia drivers but you should get the latest driver from [nvidia]("http://www.nvidia.com/Download/index.aspx?lang=en-us") website

[Check this out]("http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/"). It might help.

---

