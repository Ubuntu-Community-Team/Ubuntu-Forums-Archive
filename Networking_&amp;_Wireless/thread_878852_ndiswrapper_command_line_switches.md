---
title: "ndiswrapper command line switches"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by Frederick J. Harris on 2008-08-03
Can anyone give me a link to where I can find the command line switches for ndiswrapper?  I've checked in man and info but those sources didn't come through with decent documentation.  I've seen various ones used in example code such as -i, -l, -r, etc.  Somewhere there must be a decent list?

---

### Post by caljohnsmith on 2008-08-04
I don't know what you mean, because when I do "man ndiswrapper" it says:
```

       OPTIONS

       -i <inf file>
              installs new Windows XP driver, where <inf file> is full path to INF file for that driver.

       -l     lists the currently installed drivers.

       -e <driver>
              removes an installed Windows XP driver named <driver>.

       -m     writes  an alias for wlan0 (default wireless device) into module configuration file so that ndiswrapper kernel module  is  loaded automatically when this interface is used.

```

---

