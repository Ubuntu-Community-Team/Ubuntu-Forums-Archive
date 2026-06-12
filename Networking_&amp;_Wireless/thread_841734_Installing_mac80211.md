---
title: "Installing mac80211"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by mortenoc on 2008-06-26
In order to get the wifi on my laptop up and running, I tried to install mac80211, but upon issuing the 'make' command I got:

 make

WARNING: $SHELL not set to bash.

If you experience build errors, try 'make SHELL=/bin/bash'.

The I issued 'make SHELL=/bin/bash' but got the following:

Checking kernel compatibility in:
	/lib/modules/2.6.24-19-generic/source//
grep: /lib/modules/2.6.24-19-generic/source//include/linux/netdevice.h: No such file or directory
   ! Requires netif_tx_lock_bh ! No compatiblity patch available.

Could not provide compatible version. Try 2.6.18 or newer.

Terminating.
If patch or script failed, check pre/ and post/ for current stage.
make: *** [compatible/modified] Fejl 1 (Fejl means error in danish).

Here I'm quiet stuck. How do I proceed?

---

### Post by chili555 on 2008-06-26
Well, mac80211 is already installed. Also, if you must redo what's already done, there is an extra / in there:> /lib/modules/2.6.24-19-generic/source//Without seeing the Makefile, it's hard to know what to suggest. I'm pretty sure you do not have linux-headers installed, as well.

From my machine:> /lib/modules/2.6.24-19-generic/updates/wireless/iwlwifi/mac80211

---

