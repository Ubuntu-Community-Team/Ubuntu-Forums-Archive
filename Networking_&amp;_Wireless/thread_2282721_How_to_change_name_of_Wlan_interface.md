---
title: "How to change name of Wlan interface?"
date: 2015-06-16
forum: Networking &amp; Wireless
---

### Post by jdallara on 2015-06-16
Hello,

  Probably an easy fix but I haven't been able to find it.  All my systems call their wireless interface wlan0 EXCEPT for one which calls it wlan2.  Where is that interface name defined?  It messes with my CDO to have one system different from the others for no particular reason.

Thanks, Jon

---

### Post by chili555 on 2015-06-16
> which calls it wlan2

....

for no particular reason.There is probably a reason. You either have, or have had previously, another wireless device installed. udev assigns wlanX as needed and isn't usually purged because it isn't aware that the old card is now at the landfill.

If you have another card in the machine, I'd suggest blacklisting its driver so that wlan0 or wlan1 never gets assigned again. Then amend /etc/udev/rules.d/70-persistent-net.rules to remove unneeded listings and change the relevant listing to wlan0. If you need specific guidance, post back and we'll help.

After amending *rules*, immediately reboot.

---

### Post by jdallara on 2015-06-16
Bingo!  That was the config file.  For some reason, known only to the OS, the same interface with the same MAC address was listed 3 times, wlan0, wlan1, and wlan2.  FYI, the last entry in the file is the one that is used.

Thank you very much, saved a lot of documentation diving.

Jon.

---

### Post by chili555 on 2015-06-16
Awesome! Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

