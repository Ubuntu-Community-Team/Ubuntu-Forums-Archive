---
title: "27 seconds for firefox to start homepage"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by MeTylerDurden on 2009-12-26
Was having slow internet called service provider he said he made some change to the modem or router. I have 2 pc and on this one with xp it starts my homepage in a few seconds but on Ubuntu on other pc is almost 30 seconds.. Really not sure if the reboot of modem/router did anything or was my recent upgrade to 9.10 but still says im using 9.04.. also made big change and enabled all the repositories when I upgraded last week and was very leary about messing up my system..

---

### Post by peakshysteria on 2009-12-26
Hmm, something is way wrong that's for sure. You might find a solution on Mozillazine's: [[COLOR="Red"]Firefox hangs[/COLOR]]("http://kb.mozillazine.org/Firefox_hangs")

---

### Post by bapoumba on 2009-12-26
> **MeTylerDurden said:**
> Was having slow internet called service provider he said he made some change to the modem or router. I have 2 pc and on this one with xp it starts my homepage in a few seconds but on Ubuntu on other pc is almost 30 seconds.. Really not sure if the reboot of modem/router did anything or was my recent upgrade to 9.10 but still says im using 9.04.. also made big change and enabled all the repositories when I upgraded last week and was very leary about messing up my system..
Please try about:config in the url.
Enter ipv in the search box and make sure ipv6 is set to false.

---

### Post by lovinglinux on 2009-12-26
> **bapoumba said:**
> Please try about:config in the url.
Enter ipv in the search box and make sure ipv6 is set to false.

+1

Also, if Firefox is taken too much time to start (not to display the page), then optimize the databases. Slow starts could also be due to extensions performing heavy functions on load, specially those related to database reading/writing.

See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

