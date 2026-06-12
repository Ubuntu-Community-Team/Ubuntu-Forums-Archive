---
title: "Ndiswrapper issue"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by LastChildren on 2007-05-15
Well, I'm not exactly sure if the issue is ndiswrapper or Ubuntu itself.  I installed a Netgear WG311v3 wireless adapter using the walk-thru located here:  

[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3]("https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3")

 and everything worked fine...BUT everytime I restart the system, the Network Manager thinks the wireless apadter is no longer there!

When I run iwconfig (after restarting), wlan0 is no longer there.  I have to use "sudo modprobe ndiswrapper" in order to get the card running again (after which it works just fine).  The last instruction in the walk-thru is "sudo ndiswrapper -m" which the author claims will ensure that the driver is loaded each time the computer is booted, but it's not working.  I tried reading the man page for ndiswrapper, but there's no info there about the "-m" option or any options at all.  Can somebody please help?

Also, is there a way to configure the system so that it connects to the wireless network by default automatically each time the system boots?

---

### Post by spd106 on 2007-05-16
Try adding ndiswrapper to the list of driver modules in your /etc/modules file.

---

