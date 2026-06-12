---
title: "WPS for Ubuntu 12.04 - I think not?"
date: 2014-01-06
forum: Networking &amp; Wireless
---

### Post by Bobby_James on 2014-01-06
Does Ubuntu 12.04 support WPS at all?  I have looked in the Network Manager and cannot see anything.  In other words: can I connect to a router which has WPS enabled with my laptop?  Can I enter the PIN on the laptop which corresponds to the hard-wired WPS PIN on the router?

---

### Post by TheFu on 2014-01-07
I could be out of date with the latest information, but wasn't WPS found to be a highly broken protocol - non-secure?
[http://krebsonsecurity.com/2011/12/new-tools-bypass-wireless-router-security/](http://krebsonsecurity.com/2011/12/new-tools-bypass-wireless-router-security/)

---

### Post by r3dd on 2014-01-07
WPS is easily broken in to in just a few minutes. Unless you trust everyone who could potentially come around your network it is advisable to configure the router without WPS enabled.

---

### Post by praseodym on 2014-01-07
Hi,

neither network-manager or Wicd support WPS, but "wpa_gui" does:

[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)

For using it the /etc/network/interfaces needs to be adjusted for the respective interfaces.

---

