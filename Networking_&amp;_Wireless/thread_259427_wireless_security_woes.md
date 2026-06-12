---
title: "wireless security woes"
date: 2006-09-17
forum: Networking &amp; Wireless
---

### Post by sp0nge on 2006-09-17
I've been tiying with my wireless settings since I've managed to get my BCM43XX working. With security disabled, I am able to access this network just fine, but run into troubles as soon as ANY security configuration is changed. What do I need to do to secure my network?

---

### Post by karamba_kid on 2006-09-18
What driver is running your wifi card?  I use the package named wpasupplicant for wpa security with my card that uses the supported madwifi driver.  The man pages for wpa_supplicant (you need the _ in there to get the manuals to show up) will have a list of supported drivers.

---

### Post by sp0nge on 2006-09-18
I'm using bcmwl5 driver and ndiswrapper. This is running well, but still no luck with the WEP/WPA. Unfortunately work calls and I'll not be able to try this out until this evening but thank you for the start.

---

### Post by karamba_kid on 2006-09-18
I don't have any experience with ndiswrapper but a quick trip to google brought up this guide... [http://ubuntuforums.org/showthread.php?t=31418](http://ubuntuforums.org/showthread.php?t=31418) I hope it can help you out.  Remember that WEP is worthless so only waste your time getting WPA working :)

---

