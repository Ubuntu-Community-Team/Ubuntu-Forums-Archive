---
title: "wifi working on some access points but not all in gutsy"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by dbcoolio on 2007-10-22
This is kinda weird, but after I upgraded to gutsy, I'm able to connect to my wifi at home but not to the wifi at school.  well, sometimes I can connect, but it goes slow and eventually kicks me off.  I tried installing the restricted Firmware driver but it didn't make any difference.  I got it working for a little bit by manually configuring the wireless card, taking it out of roaming mode and forcing it to an access point, but eventually it did the same thing.  my laptop's turn wifi on/off switch works by using the function key and F2, and when the wifi quits out it turns off the LED saying that wifi is working also.


I have a Broadcom wifi card, and it was working fine in Feisty, so it should be fixable, but I'm not sure what the deal is.  I'm going to try reinstalling the driver from the script in the howto, but anyone with a better idea?

---

### Post by MegaJim on 2007-10-22
Try using wicd rather than the network manager, it seems to be working better than NM in this release.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by dbcoolio on 2007-10-24
I installed WiCD and it helped a little but didn't fix it.  I ended up reinstalling the NDISWrapper using the script from the How-to, and that got it working again (as far as I can tell)

---

