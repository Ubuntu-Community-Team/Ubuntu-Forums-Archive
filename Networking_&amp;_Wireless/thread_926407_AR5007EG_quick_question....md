---
title: "AR5007EG quick question..."
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2008-09-21
Hello,


My AR5007EG is working great with the latest madwifi-hal compiled!

However, upon reboot, I have to run 2 commands to get my wifi up and running...

1) sudo wlan_scan_sta
2) sudo /etc/init.d/networking restart

*Atheros & HAL are unchecked in the system settings manager.

Any way to automate the above, or get the system to recognize my ath0 module at boot???

---

### Post by DapperMe17 on 2008-09-22
Could I add "wlan_scan_sta" to the /etc/modules file to fix this?

---

