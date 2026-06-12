---
title: "Networking cycles from ethernet, looks for wifi, then reconnects to ethernet, repeats"
date: 2016-06-08
forum: Networking &amp; Wireless
---

### Post by raymondvillain on 2016-06-08
Ubuntu 14.04 desktop, used wifi for several months, no problem, then moved to location convenient to FIOS router, so hooked up ethernet cable.  At startup, machine connects to internet via ethernet, but in a few seconds it drops the connection and hunts for wifi (I removed the USB wifi dongle), "Disonnected, you are now offline", then in a few more seconds  it hooks back up to the ethernet successfully.

In Network Connections I have deleted the wifi connection.

Don't understand why it continues to cycle between ethernet and previous wifi connection.

Any suggestions will be greatly appreciated.

---

### Post by Zanden on 2016-06-08
Can you disable Wifi? Uncheck Enable Wifi?

---

### Post by raymondvillain on 2016-06-08
Don't see that option.  The machine no longer has wifi capabilities.  Formerly I used a wifi adapter that plugged into a USB port, now that's no longer present, so neither the Ubuntu Network app nor the Network Connections app have any mention of wifi in the text boxes.

---

### Post by raymondvillain on 2016-06-08
Now it is working correctly.  Somehow ipv6 settings had the box checked "require ipv6 for this connection..." and I cleared the check box and all seems to be well, marking this thread solved.  Thanks for everyone's input.

---

### Post by Zanden on 2016-06-09
Great.

---

