---
title: "Wireless card in monitor mode using ndiswrapper driver?"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by jbaerbock on 2007-08-10
Have ndiswrapper as my wireless driver and am trying to use Aircrack-ng utilities to put my Broadcom card into monitor mode so I can learn aircrack-ng. Any ideas on how to do this, the regular way to do it comes back and says ndiswrapper does not support monitor mode.

---

### Post by spd106 on 2007-08-13
Just as it says, ndiswrapper doesn't support monitor mode.

You can use the bcm43xx driver instead, but it won't work very well without the new mac80211 stack, which you will have to build for yourself.
See [http://linuxwireless.org/en/users/Drivers/bcm43xx](http://linuxwireless.org/en/users/Drivers/bcm43xx)

---

