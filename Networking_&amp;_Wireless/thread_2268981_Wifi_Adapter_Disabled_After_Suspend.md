---
title: "Wifi Adapter Disabled After Suspend"
date: 2015-03-12
forum: Networking &amp; Wireless
---

### Post by Gregory_Halverson on 2015-03-12
Hi, I'm running Ubuntu 14.04 on a Dell Inspiron 3135 laptop. I have this problem where the wifi adapter completely disconnects after resuming from suspend.


After booting Ubuntu 14.04 from the laptop being off, wifi works just fine, and "nmcli nm" produces:


RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         connected       enabled         enabled    enabled         disabled  


After resuming from suspend, wifi no longer works, and "nmcli nm" produces:


RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         disconnected    disabled        disabled   enabled         enabled   


"nmcli nm sleep false" produces:


Error in sleep: Already awake


How do I reconnect the wifi adapter after resume, or how do I prevent it from being disconnected and disabled on suspend?

---

### Post by Gregory_Halverson on 2015-03-12
Got it. You have to load the dell_laptop mod to unblock wifi.

sudo gedit /etc/pm/sleep.d/wakenet.sh

wakenet.sh:

#!/bin/sh


case "${1}" in
        resume|thaw)
	rmmod -f dell-laptop
	rfkill unblock all
        nmcli nm sleep false
                ;;
esac

then sudo chmod +x /etc/pm/sleep.d/wakenet.sh

Now wireless comes back on fast and on its own after suspend.

---

### Post by Gregory_Halverson on 2015-03-13
[https://github.com/gregory-halverson/dell-wakenet](https://github.com/gregory-halverson/dell-wakenet)

---

