---
title: "Screen Resolution"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by stellyfox on 2011-05-31
Hi,

I downloaded 11.04 and booted up from disk - all OK, so I went ahead and installed it.

I have a problem with screen resolution. I only have the option for 640x480 and one that's even worse! I want it to be 1024x768.

The Medion desktop previously had Vista on it. The nvidia (GeForce 7650 GS) site says that it doesn't support Ubuntu. It now only has Ubuntu on it

I can still boot from the cd and it the display is fine - it's just when I boot from hard drive. It's driving me nuts.

I'm completely new to this - can anyone help please??

Any ideas??

---

### Post by frankbooth on 2011-05-31
It sure seems weird that everything is fine when you boot from a LiveCD but not once installed. Are you sure that you haven't done any changes since installing?

Have you installed the latest proprietary drivers?
Your card should be supported in nvidia-glx-185 (Version 185).

[How to install proprietary drivers in Ubuntu.]("http://www.ghacks.net/2009/04/15/using-proprietary-drivers-in-ubuntu/")

---

### Post by wildmanne39 on 2011-05-31
> **stellyfox said:**
> Hi,

I downloaded 11.04 and booted up from disk - all OK, so I went ahead and installed it.

I have a problem with screen resolution. I only have the option for 640x480 and one that's even worse! I want it to be 1024x768.

The Medion desktop previously had Vista on it. The nvidia (GeForce 7650 GS) site says that it doesn't support Ubuntu. It now only has Ubuntu on it

I can still boot from the cd and it the display is fine - it's just when I boot from hard drive. It's driving me nuts.

I'm completely new to this - can anyone help please??

Any ideas??
Hi, boot into the system go to administration and install the additional drivers for your video card.

---

