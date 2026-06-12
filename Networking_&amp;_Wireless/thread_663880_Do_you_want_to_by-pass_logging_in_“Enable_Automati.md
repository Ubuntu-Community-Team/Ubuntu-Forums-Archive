---
title: "Do you want to by-pass logging in “Enable Automatic Login” and “keyring” passwords on"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by RustyWyatt on 2008-01-10
Howdy,

Do you want to by-pass logging in (Enable Automatic Login) and “keyring” passwords on boot-up and connecting to a network?

I recently had to reinstall 7.10 on my laptop and while getting it reconfigured to my needs I found a VERY simple way to accomplish the above!

GoTo: [http://wicd.sourceforge.net](http://wicd.sourceforge.net)

Download WICD and follow the simple instructions. This has been working for me exactly as described above and with no problems or complications that I have found yet!

Good Luck,

Tom

---

### Post by magozoom on 2008-01-12
WICD manager is really great - it's available in Synaptic / Gutsy as version 1.3.1 and works perfect. I was unable to build the downloaded version fromsourceforge, but the version in the repository worked fine. 


The entry in the "Sessions"  manager to autostart WICD should be /opt/wicd/tray-edgy.py, 
**not /opt/wicd/tray.py** as in the README 

Installing  WICD uninstall nm-applet, after installation there is no network - restarting the session enables WICD.

---

