---
title: "kismet"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by zmzach on 2008-11-29
Trying to get kismet goin on my computer, and I can't figure out what my sources should be:

zach@zak-computer:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'madwifi' in source 'madwifi,ath0,kismet'
Done.


I have an IBM thinkpad T60 with an intel 3945 a/b/g wireless card. Kinda lost here . . .

---

### Post by zmzach on 2008-11-29
I figured out which source I should be using (ipwlivetap), but now I'm getting this error message:

zach@zak-computer:/etc/kismet$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (kismet): Enabling monitor mode for ipwlivetap source interface ath0 channel 0...
FATAL: Failed to open ipw sysfs tap control file, check that the version of the ipw drivers you are running is recent enough, and that your system has sysfs properly set up.
Done.

Again . . . I'm stumped.

---

