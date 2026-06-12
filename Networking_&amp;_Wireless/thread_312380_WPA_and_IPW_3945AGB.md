---
title: "WPA and IPW 3945AGB"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by rshol on 2006-12-04
Setup

Dell Latitude D820

Wireless Card
IPW 3945AGB

Buffalo WBR2-54G wireless access point
Configured for WPA-PSK personal essid is not broadcast
 
Clean install of Ubuntu 6.1 with updates

Installed network-manager and network-manager-gnome
Insured wpasupplicant was installed.
Insured linux-restricted-modules-generic was installed

I referred to the following resources in trying to set wpa up.

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_get_ipw3945_and_wep.2Fwpa_to_work](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_get_ipw3945_and_wep.2Fwpa_to_work)

After all that, the system refuses to connect to the wireless network.  I click on the network-manager icon in the notification area, select set up a new wireless network, enter the essid and the key.  I am not prompted for a keyring password and the network-manager throbber spins endlessly.

What must I do to enable wpa access?

---

### Post by rshol on 2006-12-04
No clues?  WPA is a deal killer for me.  Without WPA I can't get on the company network.  Without network access I'm being held hostage by windows.

---

### Post by rshol on 2006-12-04
Bump.

---

### Post by aztektum on 2006-12-14
don't know if you figured it out yet, but this worked for my IPW2200

[http://www.ubuntuforums.org/showthread.php?t=263136](http://www.ubuntuforums.org/showthread.php?t=263136)

i was trying to use -Dipw but it wouldn't work. this one specifies -Dwext haven't learned why yet.

---

### Post by n00b@linux on 2006-12-14
Don't bother with wpa-supplicant.  If you follow the links you'll see your ipw3945 is nor supported.   Try this lnk instead: 

[http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

It has an 80% success rate.  It worked for me.

---

