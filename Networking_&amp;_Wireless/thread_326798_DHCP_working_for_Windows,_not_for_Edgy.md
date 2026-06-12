---
title: "DHCP working for Windows, not for Edgy"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by Enselic on 2006-12-28
I am at a friends house, and he have a cable modem.

On his computer using Windows XP, he can obtain an IP from the modem using DHCP.

On my laptop, using Ubuntu Edgy Eft, I am unable to maintain an IP however.

DHCP works perfectly fine at home, so could it be something cheesy with the cable modem?

He keeps humiliating Ubuntu because of its "broken DHCP support", so it would be nice to fix this 8)

---

### Post by dbott67 on 2006-12-28
Are you using wired or wireless?  Any encryption (WEP/WPA)?

```
sudo ifdown <if#> && sudo ifup <if#>
```

replace <if#> with the appropriate interface (eth0, eth1, wlan0, ath0, etc.) 

Also, you can just use **sudo dhclient** to obtain an IP address.

-Dave

---

### Post by Enselic on 2006-12-28
Thanks for the reply but we figured out was was wrong.

The problem was solved by turning off the modem for a while. The tele-station that gives IP addresses locks to a specific MAC adress unless one turns off the modem and waits for a while, which resets the "lock".

---

### Post by haiku99 on 2006-12-28
interesting!   I didn't know that was possible, but suspect something similar is happening w/ a Zoom 5615 DSL modem I've been fighting with....

---

