---
title: "nm-applet dhcdbd problem"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by dbu on 2008-05-10
x86_64 ralink rt2500 wireless / wpa2 network was working fine in Gutsy, and the first week after installing Hardy.  No changes whatsoever to network or access point or other machines on the local net.

Now spontaneously 'roaming' mode will not work with wireless; signal-bars appear but are all grey.  IWCONFIG reports successful association w/ access point but there is no real link as dhclient fails.  Manually setting local wlan0 IP and attempting to ping AP also gets 'no route to host'.

Reverting to 'Manual Net Config' with all the same wpa2 settings works fine.

Only differece between manual-config'd output of iwconfig and the roaming version is that 'roaming' claims that EncryptionKey is 'off'.  Even though dialog box of nm-applet/Edit-Wireless-Config claims that it is WPA2.  Which it at least at some point must have gotten right in order to associate with the AP in the first place.

Anyone have a theory?  It works with all the duct-tape&string of having to disable roaming every time I come home .. all of which setup it conveniently chooses to throw away every time I switch back to roaming.

---

