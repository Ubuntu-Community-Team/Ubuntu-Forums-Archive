---
title: "[Ubuntu 7.10] Can't change Wi-Fi adapter mode"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by slash213 on 2008-04-06
Hi, guys. Nice to meet you. :)

Ran into confusing situation. I've got Asus eeePc (wi-fi adapter: Atheros AR5006EG) and a fresh Ubuntu 7.10 Gutsy installation from LiveCD. Default proprietary wi-fi drivers don't work for eeePc, so I had to use madwifi module, and now wireless connection is detected by system, but with one issue.

My adapter can work only in one mode: managed. Any attempt to change it (through /etc/network/interfaces/ config, iwconfig or gnome-network-manager) gives me an:

'Error for wireless request "Set Mode" (8B06) :
SET failed on device ath0 ; Invalid argument.'

Been googling the problem for an hour now and couldn't find a solution. Everything works fine in managed, but, well, I want to have a use from ad-hoc and monitor modes at least.
Thanks in advance.

---

### Post by spd106 on 2008-04-06
Have you tried installing the madwifi-tools package? I think you're going to need to use the wlanconfig tool from that package.

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)
[https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi](https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi)

---

### Post by slash213 on 2008-04-06
> **spd106 said:**
> Have you tried installing the madwifi-tools package? I think you're going to need to use the wlanconfig tool from that package.

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)
[https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi](https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi)

Thanks! wlanconfig was already installed and solved my problem.
Well, it's not very comfortable, but it's working.
For others having the same problem (don't type in '%'s, of course):

%wlanconfig ath0 destroy
%wlanconfig ath0 create wlandev wifi0 wlanmode adhoc

Creates ath1 interface with Ad-Hoc mode locked.
After that you can destroy ath1 and recreate it in any needed mode.

---

