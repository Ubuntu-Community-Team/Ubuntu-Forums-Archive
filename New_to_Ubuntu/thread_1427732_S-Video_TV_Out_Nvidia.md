---
title: "S-Video TV Out Nvidia"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by MobiusJedi on 2010-03-11
On XP, I had the problem with black and white through the s-video. I lowered the color depth on the tv display to 16-bit and got color. (I still can't get my nvidia's tv-out working properly on Ubuntu though...)

---

### Post by overdrank on 2010-03-11
Hi and welcome. I have moved your post to its own thread. No need to bump a 2 yr old thread. :)

What is the model of the nvidia graphics card? You can use the command ```
lspci | grep VGA
``` In the terminal to Identify your hardware. The terminal is located under applications, accessories.

 Have you tried the command ```
gksu nvidia-settings
``` using the alt, F2 to detect the monitor via the s-video?

What version of Ubuntu are you using? You can find this under system, About Ubuntu.


Moved to Absolute Beginner Talk

---

