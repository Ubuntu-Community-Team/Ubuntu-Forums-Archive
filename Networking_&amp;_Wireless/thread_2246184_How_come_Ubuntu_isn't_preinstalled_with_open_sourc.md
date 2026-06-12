---
title: "How come Ubuntu isn't preinstalled with open source Broadcom drivers?"
date: 2014-09-29
forum: Networking &amp; Wireless
---

### Post by argonvegell on 2014-09-29
Just wondering that all, if 'firmware-b43-installer' is an open source driver, how come it's not preinstalled?

---

### Post by varunendra on 2014-09-29
It is not a driver, it is a tool to get the proprietary firmware that the opensource driver needs.

The procedure to find and install the required firmware is part of the installation of the firmware-b43-installer package itself, so it won't do that if it is preinstalled. Besides, putting any such thing that may automatically download and install the proprietary firmware without user action, may potentially break Broadcom's Licence policy.

In short, it is legal for a user to download and install the proprietary firmware/driver, but is not okay if Ubuntu or any other OS does it automatically without a legal Licence agreement with Broadcom. So.. neither the firmware, nor the "wl" driver can be distributed with Ubuntu.

The really opensource drivers - b43 (reverse engineered, depends on proprietary firmware) and brcmsmac/brcmfmac (fully opensource, doesn't need proprietary firmware) are parts of the kernel, or in other words, "Preinstalled".

---

