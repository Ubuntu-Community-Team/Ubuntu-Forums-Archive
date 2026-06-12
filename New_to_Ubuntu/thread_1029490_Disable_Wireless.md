---
title: "Disable Wireless"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by transmition on 2009-01-03
How would I go about disabling wireless internet? Is there anything I can pkill?

I am running 8.10 on a macbook 4,1.

---

### Post by DarkReaper79 on 2009-01-03
Is there a key combo you can do to shut it off. On my dell its the fn key with F2. Or you can try to right click the network icon, and uncheck enable wireless. Hope this helps.

---

### Post by lswb on 2009-01-03
If you don't have any type of hardware control and want to completely disable it you can blacklist the driver for your wifi adapter. 

To disable it temporarily, if using Network Manager, right click on the NM icon and check/uncheck "Enable Wireless" as desired.

From the command line you can use "sudo ifconfig wlan0 down", substituting the correct interface name for "wlan0" and "sudo ifconfig wlan0 up" to reenable. Note that if Network Manager is running, it can reenable the interface without needing to use "sudo ifconfig ..."

---

