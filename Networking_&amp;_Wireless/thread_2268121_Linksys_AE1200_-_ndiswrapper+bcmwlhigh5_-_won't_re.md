---
title: "Linksys AE1200 - ndiswrapper+bcmwlhigh5 - won't reconnect after suspend"
date: 2015-03-06
forum: Networking &amp; Wireless
---

### Post by oldguysrule on 2015-03-06
Using xubuntu on an older system - dual core athlon64.
Managed to get the Linksys wireless adapter working using info from forums etc to install ndiswrapper and bcmwlhigh5 driver.
My issue is that when I use suspend the connection is lost and I cannot recover it unless I reboot.
I have tried sudo modprobe etc. without success, Same with nmcli nm. 
killall NetworkManager does nothing
/etc/init.d/networking restart  and permeations of restart networking-manager, if up etc do not work.
tried editing /etc/pm/sleep.d/wakenet.sh - no joy.
edited /etc/pm/config.d/unload_modules with various configurations of SUSPEND_MODULES="SUSPEND_MODULES ndiswrapper+bcmwlhigh5" but it still will not reconnect after suspend.
Any thoughts on how to resolve this. I hate to have to reboot all the time.

Thanks

---

