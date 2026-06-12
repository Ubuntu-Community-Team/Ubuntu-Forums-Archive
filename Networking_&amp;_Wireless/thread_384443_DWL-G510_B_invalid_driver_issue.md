---
title: "DWL-G510 B invalid driver issue"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by dRock1286 on 2007-03-14
So I have tried about every different possible solution to getting my wireless pci card, DWL-G510 (B), to work.  I tried to install the driver via ndiswrapper and madwifi.  Then, when I do

> ndiswrapper -l

I get something to the extent of...

> neta3ab invalid driver

Anyone know how to fix this?

---

### Post by spd106 on 2007-03-14
This card should work with madwifi according to [http://madwifi.org/wiki/Compatibility#DWLG510](http://madwifi.org/wiki/Compatibility#DWLG510). 

Could you please post the output of this command
```
sudo lshw -class network
```

Have you been able to scan for access points? Assuming you have madwifi loaded, try running this command ```
sudo iwlist ath0 scan
```

---

### Post by dRock1286 on 2007-03-14
Sorry...I got it all worked out now.  I posted how on my "Uninstalling Ubuntu, Installing other Linux Distro" thread.  Thanks though.

---

