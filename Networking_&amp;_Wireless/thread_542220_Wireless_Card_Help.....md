---
title: "Wireless Card Help...."
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by svtguy88 on 2007-09-03
I figured out that by adding "break=top" to the options for boot up (WAY in the beginning of the other options) and then following the other steps outlined on a link suggested to me in another thread, it works. I can now boot into Ubuntu and Vista without any issues. However, my wireless card isn't recognized. It is an Intel 4965, but the drivers for the 3945 are supposed to work (which are apparently built into Ubuntu already).....any ideas?

---

### Post by svtguy88 on 2007-09-04
Anybody?

---

### Post by noob12 on 2007-09-04
What release are you running?

Feisty has the ipw3945 driver.  I don't think it will work as shipped for the 4965 and it won't claim it by default.

I've heard that Gutsy Tribe 4 (note: pre-release) and later has 4965 support.

[http://intellinuxwireless.org/](http://intellinuxwireless.org/) has an iwlwifi driver that would work, but you need to build it, and it is still considered in dev stage.

ndiswrapper + your windows driver will probably work with Feisty.

---

### Post by svtguy88 on 2007-09-04
Really, it won't recognize the 4965?  I thought I saw on some chart somewhere that the 3945 and 4965 are basically compatible....I guess I'll get to work with ndiswrapper....

---

