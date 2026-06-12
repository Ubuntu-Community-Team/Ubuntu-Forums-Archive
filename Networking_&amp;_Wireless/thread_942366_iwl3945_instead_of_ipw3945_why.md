---
title: "iwl3945 instead of ipw3945 why?"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by s_force on 2008-10-09
Hi everyone!

i typed in:
sudo airmon-ng start wlan0 5

and it says, wlan0 - iwl3945 and so on.

Why? I have the following card:

```
Intel PRO Wireless 3945ABG
```
And that fits to the driver ipw3945!

And why there is the wrong driver? That works, but only airmon doesn't!

Is there a way to change the driver for that device?

Thank you!

---

### Post by iceberg303 on 2008-10-25
open source iwl3945 drivers replaced the closed source iwp3945 drivers.

aircrack-ng and thus airmon-ng do not support this driver at current time. If you want to use the iwp3945 drivers you will hae to remove the iwl drivers and make sure you have an old enough kernel to use the iwp drivers and build them from scratch.

---

