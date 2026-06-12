---
title: "Beelkin  Wireless G card won't work"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by Norman Thom on 2009-06-13
I have just installed a Belkin 802.11 wireless card in Ubuntu 9.04
According to the device manager the computer sees the card as a wlan device of unkown manufacturer.  Checking the card in the computer there are no lights indicating that it is working.  I'm wondering if this is a driver problem or simply an incompatibility between Belkin and Ubuntu. Are there any suggestions.

Thanking you in advance

concerned

---

### Post by FreewheelinFrank on 2009-06-13
Ubuntu 8.10 and 9.04 have better support for Belkin cards.

Maybe try a live CD to test if a later version works with the card?

---

### Post by Norman Thom on 2009-06-13
Thanks FF

Tried to run live cd of 9.04 to no avail.
Would not even display.  Is there other options

Norm

---

### Post by synapsys on 2009-06-13
Open up a terminal and type:

```
lspci | grep Wireless
```

and post output here.

---

### Post by TeoBigusGeekus on 2009-06-13
Try wicd.

---

