---
title: "Acer AL1706 monitor &amp; Ubuntu"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by Bambi429 on 2009-06-20
Hi there! I'm new to Ubuntu, and am having a bit of trouble with my monitor. I installed Ubuntu 9.04 on my Acer Aspire (monitor model is AL1706). Everything is enlarged. 

When trying to get into display I get this message:

It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?

Click Yes & get this: 

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

I can't change the resolution size, because my monitor is 'Unknown'.

Can someone please walk me through this? Is there something I'm missing?

Thanks in advance!

---

### Post by TeoBigusGeekus on 2009-06-20
Have you enabled the proprietary drivers for your system?
If not, go to System->Administration->Hardware Drivers and see if there is a driver for your video card.

---

### Post by Bambi429 on 2009-06-20
Thank you :)
I followed the directions you gave me, and nothing is activated. I had done this once before, when I first installed and tried to activate the recommended. When restarting, I had a gray box floating on the screen. I can't remember what it said, but the bottom line was that it was no good. Should I try one of the other settings?

---

### Post by TeoBigusGeekus on 2009-06-21
Yes. Some screen shots with options and/or messages would be welcome.

---

### Post by Bambi429 on 2009-06-21
As suggested, I tried another option (did NVIDIA accelerated graphics driver v. 173 first) and on restart got the 'Input not supported' box, so I then tried NVIDIA accelerated graphics driver v. 96 & was successful! I was able to go into display, and change the resolution size. Thank you so much for your help!   :KS

---

