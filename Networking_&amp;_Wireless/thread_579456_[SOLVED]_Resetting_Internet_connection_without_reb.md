---
title: "[SOLVED] Resetting Internet connection without rebooting?"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by mivo on 2007-10-18
The subject title may not accurately describe my problem, so let me briefly explain what the trouble is:

My computer is connected to a ADSL router/modem (which acts as a DHCP server). This works just fine, but after resetting the router (i.e. after a short DSL outage, the router losing power, or me plugging it out for a moment), Ubuntu will be unable to connect to the Internet until I reboot the machine. I assume this is because the dynamic IP address changes? Since I'm currently in the process of trying to set up a new router (which also acts as DHCP) and it is having issues to sync with my ADSL (that is specific to the new device and unrelated to my question), I have to reboot Ubuntu every time I plug my working router back in after a failed attempt to get the new device to work with my DSL splitter.

This is probably simple, but how do I get Ubuntu to request a new IP address/reset the Internet connection without having to completely reboot of the system?

---

### Post by NilsE on 2007-10-18
try the following in a terminal.  It should force the refresh of the IP address.

sudo dhclient

---

### Post by mivo on 2007-10-18
This worked! Thanks so much. :) Also got that new router, a D-Link G684T, to work (more or less). It needed a firmware update and "Virtual Circuit" enabled.

---

### Post by pizpot on 2008-02-28
I found a better way for my wireless laptop... right-click on network manager icon in tray and un-check "Enable Networking" then turn it back on.

---

