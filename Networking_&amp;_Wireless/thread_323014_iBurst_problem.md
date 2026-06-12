---
title: "iBurst problem"
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by nortis on 2006-12-21
I'm using Breezy 5.10 and tried to install my iBurst pcmcia modem using the information on the wiki  [https://help.ubuntu.com/community/MobileWirelessBroadband]("https://help.ubuntu.com/community/MobileWirelessBroadband")
I followed everything step by step.

I the installation of the driver seemed to be done ok, and when I put the modem in the PC the light turns from purple to blue. However when I type```
lsmod | grep ib_
``` nothing is listed.

If I then try ```
sudo ifup ib0 
```
I get the error
```

ib0: ERROR while getting interface flags: No such device
Failed to bring up ib0

```

Thanks

---

### Post by Nitrogen on 2007-02-01
See if you can get your self a copy of Edgy Eft. I never got my pcmcia modem to work with any previous versions of ubuntu. Edgy Eft seems better all round.

---

