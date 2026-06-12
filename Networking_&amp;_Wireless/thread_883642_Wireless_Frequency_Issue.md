---
title: "Wireless: Frequency Issue?"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by t1n0m3n on 2008-08-08
Dell Precision M90 -Ubuntu 8.04/Core2Duo T7400/Intel 3945 Wireless/200G 7200rpm HD/2G 667mhz Ram/Quadro FX2500M

I boot up.
Connect to an 802.11a network just fine.
Switch to an 802.11b network
I am no longer able switch back to 802.11a until I reboot my laptop.

"/etc/init.d/network restart" does not fix
I have tried to set all of the parameters manually with iwconfig, but no luck.

iwlist scanning no longer shows the 802.11a ap.

I can't figure out if it is a Network Manager issue (I have seen some refresh bugs that might look related.) or a driver issue.

I have tried to search for something similar, but I haven't had any luck yet.

Anyone have suggestions on where to start looking for a fix?

---

### Post by caljohnsmith on 2008-08-08
Just an idea, but have you tried:
```
sudo ifdown <interface>
sudo ifup <interface>
```

---

