---
title: "Modem"
date: 2005-11-16
forum: Networking &amp; Wireless
---

### Post by nkobel003 on 2005-11-16
Well, I am having trouble connecting my modem--I assume it is incompatible, but when I try to find the right port for it (ex. dev/modem) and select autodetect, it says it could not find a modem and to check to make sure it is plugged in.  Do I need a new modem?  Do you know which internal modems I can get?  No, I cannot get high speed because of my area, and i can only connect at a maximum of 33kbps.
Thanks,
Nick

---

### Post by paddyg on 2005-11-16
i'd use an external (serial) modem. Internal (PCI) modems are usually windows-based (winmodems), and just an endless chain of woes

---

### Post by nkobel003 on 2005-11-16
Thanks, well then, if I should'nt get an internal modem, which external modem should i get?

---

### Post by migueljacq on 2005-11-16
Doesn't largely matter what brand. Any serial modem should work, it just uses the COM ports in the back of the box. paddyg is right, internal PCI modems are a lot of trouble and not worth it.
I use a SwannSmart 56K. Incidentally, the failure of the autodetect doesn't necessarily mean it won't work: a lot of people with serial external modems can't get the autodetect to work either. However, in this case, just manually try either ttyS0 or ttyS1. One of the two should work. /dev/modem will only work, I believe, if the symbolic link has been set as such.
Of course make sure you run pppconfig and set it all up right and it should be fine.

---

