---
title: "ATI/AMD Proprietary FGLRX graphics driver"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by PlasticRoadie on 2009-04-19
I've been having issues with activating this driver for a little bit now. At first it wouldn't activate at all, and said that another driver was being used in place of it. After restarting I tried again to activate the driver and now its saying that I have it disabled, and once again its not letting me activate the driver. I duno if anyone else has had this problem before, and any advice I can get on the matter would be highly appreciated.

---

### Post by ptn107 on 2009-04-20
You can try to manually install it.
```
sudo apt-get install xorg-driver-fglrx
```

---

### Post by PlasticRoadie on 2009-04-20
I tried that and it told me that the driver was the newest one, but it still won't let me active the fglrx driver in the hardware drivers thing. It keeps telling me that a different version of this driver is in use.

---

### Post by Michael.Godawski on 2009-04-20
hi PlasticRoadie,

I would try out EnvyNG to de-install the current drivers and install the newest ones.

[LIST]
[*][Official EnvyNG site]("http://albertomilone.com/nvidia_scripts1.html")
[*][How to install EnvyNG]("http://albertomilone.com/envyngfaq.html#A")
[/LIST]
It helped me once I had some issues with my ati card. Worth a try.

---

### Post by PlasticRoadie on 2009-04-20
Thanks for that Michael I installed it and it didn't show up in my systems tools tab, so I restarted and it still wasn't there I have since uninstalled and reinstalled it and have yet to find it in my systems tools tab. So I'm going to check the site for any known bugs but if you have any ideas I would love to hear them.

---

### Post by alphacrucis2 on 2009-04-20
> **PlasticRoadie said:**
> Thanks for that Michael I installed it and it didn't show up in my systems tools tab, so I restarted and it still wasn't there I have since uninstalled and reinstalled it and have yet to find it in my systems tools tab. So I'm going to check the site for any known bugs but if you have any ideas I would love to hear them.

Which version of Ubuntu are you running?

---

### Post by PlasticRoadie on 2009-04-20
8.10 but I have since fixed the problem, thanks to everyone for all their help and quick responses.

---

### Post by jhd121 on 2009-05-10
How did you fix it?  I have the same problem.

---

### Post by HavocXphere on 2009-05-10
I ended up doing a manual installation following this page:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually)
(Involves quite a bit of command line stuff. Driver from ATI page, not ubuntu server...there seem to be slight differences)

And 3D games now work fine. However some desktop effects are very slow (maximize windows) and there are rendering glitches in 2D like when scrolling in firefox.:???: [Card: ATI 3850]

---

### Post by hadriel140 on 2009-11-21
hey uhm sorry if im posting on a dead thread but uhm im running ubuntu 9.10 and am trying to install the ati/amd propriety drivers but it loads about a quarter of the way in less then a second and the hangs there...also i cant install 64-bit amd architecture items such as crossover pro 8. any ideas?

---

