---
title: "HP compaq nx 6325, no wireless"
date: 2014-01-07
forum: Networking &amp; Wireless
---

### Post by Dmoog on 2014-01-07
Hello,

have old HP compaq nx 6325 laptop. It's my wife's work machine and was still running XP so pretty much unusable. I said I would rescue it for her by switching to Ubuntu which I've been using for years. New install of 12.04, all fine, internet works no problem with ethernet cable, but the wifi won't work at all.

When I run 'Additional Drivers', it finds 'Broadcom STA wireless driver', but I can't activate it - it simply says 'Sorry, installation of this driver failed'.
This might be because the built in wireless card seems to be turned off - there's a button on the keyboard to activate or deactivate it, but it now does nothing. Possibly it's just died, possibly it can't be detected without a driver?

I've also tried a USB wireless adapter - TP Link TL-WDN3200. Not detected when I plug it in and all the workarounds I've found online seem to apply to Ubuntu 10.

Any help would be hugely appreciated!

---

### Post by chili555 on 2014-01-07
> it simply says 'Sorry, installation of this driver failed'.Sometimes, that means, roughly, "Oops! Wrong driver for the wrong device. Sorry!" Let's see what you really need and get it fixed. Please open a terminal and run and post:```
lspci -nn | grep 0280
```

---

