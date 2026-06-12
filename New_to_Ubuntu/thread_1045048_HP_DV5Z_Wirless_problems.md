---
title: "HP DV5Z Wirless problems"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by blithen on 2009-01-20
Well as the title says I have a major lack in wireless on my new laptop. From what I can tell the wireless chipset is Atheros AR5009 802.11a/g/n WiFi Adapter.

---

### Post by blithen on 2009-01-24
Also Madwifi does not seem too work

---

### Post by blithen on 2009-01-26
Anyone?? I'm still having no progress.

---

### Post by blithen on 2009-02-05
Turns out my wireless card is actually Atheros AR5007 802.11b/g WiFi Adapter. So if that changes anything please let me know, I still have no wireless internet on my laptop.

---

### Post by blithen on 2009-03-10
OKAY! I have progress!
So it seems that everything is working, except when i type in my security information to connect to my router, it sits there for about 5 minutes then pops up with the same thing again. Anyone have any way around this?

---

### Post by blithen on 2009-04-05
Guys...seriously, please help.

---

### Post by lkraemer on 2009-04-06
You haven't told the folks anything yet.....except guessing at
what your is...... Have you searched the forum yet?

Open a Terminal Window and do:
```

lshw -C network
ndiswrapper -l
iwconfig
lsmod


```
Please post the output of the above.

GOOGLE & SEARCH are your friends.  Search the forum for
"HOWTO: & AR242x" and you will locate several guides for
installing your Wifi Drivers.

lkraemer

---

