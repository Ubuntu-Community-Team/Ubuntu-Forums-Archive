---
title: "IPW2200 randomly disconnecting"
date: 2005-09-19
forum: Networking &amp; Wireless
---

### Post by luffy on 2005-09-19
On my laptop, Hoary used to run just fine, however when I reinstalled due to some issues I experienced a few problems with the package manager. I got a few errors while trying to upgrade my system, but the were resolved using apt-get -f install.
To my grief I found out that network-admin had been uninstalled, and I found no way of reinstalling it. I downloaded GTKWifi, which worked fine, but now my card randomly disconnects (probably when dhclient tries to renew my IP).
I can see the network, I can use the networkcard to scan for other networks, but I just cannot connect to any. I can reload modules, bring the card up and down to no effect.
Anyone had the same problem? I don't wanna do a reinstall _again_ :(

---

### Post by hod139 on 2005-09-19
You probably need to upgrade the driver.  See 
[http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)
ignoring the wpa stuff.

---

### Post by eraclito on 2005-09-19
[QUOTE=hod139]You probably need to upgrade the driver.  See 
[http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)
ignoring the wpa stuff.[/QUOTE]

i've got the last driver, but still have some problems:

my card disconnects when i use synaptic (and probably whet i make big download) and afet a few second it connect again.. :-? 

not big trouble, but it annoy me...

eraclito

---

