---
title: "Graphics card causing crashes"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by japhyr on 2009-10-03
Hello,

I have a System76 laptop, with an nVidia graphics card.  The graphics card seems to be causing crashes.  To make sure it was the graphics card, I ran a test using glxgears.  I started three instances of glxgears, and watched the temperature using nvidia-settings.  Through the course of about five minutes, the temperature steadily climbed from 80 to 110 degrees, then it did a hard crash.  I can repeat this process as often as I like, with anywhere from 3 to 7 instances of glxgears causing a hard crash when the gpu core temp reads 110.

I am wondering if this problem has something to do with calibration.  When I turn the computer on after being off for about 4 hours in a 65F room, the temperature sensor for nvidia settings immediately reads 60C, and climbs to 80C as the computer idles.  The computer gets warm during the glxgears test, but does not seem excessively hot.  The computer is new, there are no dust issues, and the computer is running on a flat hard tabletop.

Graphics card and driver:
lspci | grep VGA: nVidia Corporation Device 06ec (rev a1)
from nvidia x server settings: driver version 180.44

I have posted this question in the System76 forum, but that forum doesn't see a whole lot of action on the weekend.  Also, I am thinking this might be a more general issue that someone might be able to offer some insight on.

---

### Post by japhyr on 2009-10-04
Bump.  Anybody know a way to check the calibration of the thermal sensor that nvidia-settings uses?

---

