---
title: "Generating power_on_hours in terminal using SMART"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by paulchinnz on 2009-01-29
Hi complete SMART/terminal noob, related to the infamous HDD killing bug, just trying to find out the number of hours my laptop's been running.  Have tried

smartctl -A /dev/hda

but get this:

smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Smartctl open device: /dev/hda failed: No such file or directory

Thanks!

---

### Post by paulchinnz on 2009-01-29
Hmm must be missing some list of codes somewhere, anyway found this which did the trick:

sudo smartctl -a /dev/sda | more

---

