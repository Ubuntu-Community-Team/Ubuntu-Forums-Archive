---
title: "Does Ubuntu support WiFi N standard (300 Mb/s)?"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by jespdj on 2007-10-13
I just bought a Wireless N router yesterday (by NetGear). My laptop has the new Intel 4965 AGN WiFi module, which supports the draft 802.11n standard with wireless speeds up to 300 Mbit/s.

On Windows Vista it now works in high-speed mode, it says the speed of the network is 130 Mbit/s.

On Ubuntu 7.10 (beta + all the updates) the connection works, but the speed is 54 Mbit/s (so it looks like it is using the older 802.11g speed). According to the connection properties, I'm using the iwl4965 driver.

Does Ubuntu support 802.11n speeds, and if yes, how do I get it to work at a higher speed?

---

### Post by kevdog on 2007-10-13
NO (not yet)

---

### Post by jnovinger on 2007-10-13
I don't believe it does natively yet.

However, during a research project this summer we did use the Linksys WUSB300N 802.11n USB adaptor with Ubuntu and Red Hat via the ndiswrapper utility.

ndiswrapper uses the adapters Windows drivers and provides a wrapper around it that Linux can use.  I found this thread to be really helpful.
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=530772](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=530772)

Jason

---

### Post by jespdj on 2007-10-14
Thanks for the replies.

I'll just wait until the Linux drivers are updated. My Internet connection is way slower (6 Mbit/s) than my WiFi connection anyway; the high speed would only be nice for sharing data with my desktop computer, which is connected to the router with a network cable.

---

