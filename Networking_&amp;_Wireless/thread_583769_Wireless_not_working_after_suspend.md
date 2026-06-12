---
title: "Wireless not working after suspend"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by oysteinhermansen on 2007-10-20
PC = Thinkpad (Lenovo) Z60m
Wirelesscard = Intel Wireless 2200 (module ipw2200)

Networking worked straigt out of the box. But after going to suspend and then back alive, wireless stops working.

Ubuntuversion = 7.10.  New install.

Any clues ?

---

### Post by campaigner444 on 2007-10-26
I am having the same issue with my Toshiba Satellite M55-S325. I does not happen all the time, but I can get it to work if I use **Wifi-radar** after I resume the computer. Does anyone have a solution to this problem. I would rater use the built-in software rather than software from the repositories.

---

### Post by bluetoad on 2007-11-01
See Suspend Support at [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by brharri1 on 2007-11-15
Thanks bluetoad, the instructions on that page worked great for me on my acer aspire 5570z using ndiswrapper. 

create a file called /etc/acpi/suspend.d/07-network-manager.sh and in it put 

#!/bin/sh
/etc/dbus-1/event.d/25NetworkManager stop


then create a file called /etc/acpi/resume.d/63-network-manager.sh and in it put

#!/bin/sh
/etc/dbus-1/event.d/25NetworkManager start

---

