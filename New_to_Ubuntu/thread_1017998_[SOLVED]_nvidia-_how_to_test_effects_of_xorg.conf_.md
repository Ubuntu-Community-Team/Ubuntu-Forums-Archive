---
title: "[SOLVED] nvidia- how to test effects of xorg.conf changes?"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by minsf on 2008-12-21
at last, i was able to install the nvidia 96.43.09 driver on ubuntu 8.10. yay!
i have geforce4 440 ge. (Dell Latitude C840)
(i downloaded package0 straight from nvidia. the main trick was a magic line: Option "UseDisplayDevice" "DFP" in the display section in the xorg.conf)
now i want to play with the xorg.conf settings- trying to optimize them.

[COLOR="Red"]Q:[/COLOR] what's your favorite method to test the performance of each setting? sure, some times things look a bit faster than other times, but i need something quantitative...

---

### Post by DieB on 2008-12-22
"glxgears -info" in a terminal (Alt+F2:gnome-terminal)

---

### Post by igknighted on 2008-12-22
[http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/)

---

