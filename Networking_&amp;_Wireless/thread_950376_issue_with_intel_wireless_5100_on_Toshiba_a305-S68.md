---
title: "issue with intel wireless 5100 on Toshiba a305-S6898"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by Brickedin21 on 2008-10-17
hello, i just got a new laptop and went to go install 8.04 on it and it is not showing any wifi links at all. all it shows is wired connection and manual setup... not sure what to do... is there a driver or something i can download on my vista partition and then put it on a flash drive and run it?

---

### Post by Ævar Arnfjörð Bjarmason on 2008-10-17
You need to install a distribution with a 2.6.27 kernel to use the 5100 card, just get the [8.10 beta](http://www.ubuntu.com/testing/intrepid/beta) which has a 2.6.27 kernel and it should work out of the box, [I'm using a 5100 wireless card right now](http://ubuntuforums.org/showthread.php?p=5983627) under 8.10.

Or, if you insist on running 8.04 you can [try to backport the driver](http://ubuntuforums.org/showthread.php?t=879134), not worth the effort though as 8.10 will be out officially in a few days anyway.

---

### Post by yeeking on 2009-07-06
> **Ævar Arnfjörð Bjarmason said:**
> You need to install a distribution with a 2.6.27 kernel to use the 5100 card, just get the [8.10 beta](http://www.ubuntu.com/testing/intrepid/beta) which has a 2.6.27 kernel and it should work out of the box, [I'm using a 5100 wireless card right now](http://ubuntuforums.org/showthread.php?p=5983627) under 8.10.

Or, if you insist on running 8.04 you can [try to backport the driver](http://ubuntuforums.org/showthread.php?t=879134), not worth the effort though as 8.10 will be out officially in a few days anyway.

That's what you think... I want a combination of the following:
1. stable rt kernel
2. ati proprietary driver
3. working intel 5100

And right now, 8.04 has the first two but not the last, without said effort. 8.10 has 2, 3. 9.04 has 2, 3. 

best

Matthew

---

