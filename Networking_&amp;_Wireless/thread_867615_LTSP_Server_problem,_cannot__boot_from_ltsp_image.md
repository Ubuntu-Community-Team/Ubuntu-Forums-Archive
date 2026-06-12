---
title: "LTSP Server problem, cannot  boot from ltsp image"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by mixersoft on 2008-07-23
I'm using the 8.04 LTSP Server from the QuickInstall howto. I get the pxe boot image from dhcp just fine, but it hangs on boot. This is the error message:

[] NET: Registered protocol family 17
ipconfig: eth0: SIOCGIFINDEX: No such device 
ipconfig: no devices to configure
/init: .: Can't open /tmp/net-eth0.conf
[] Kernel panic - not syncing: Atempted to kill init!

eth0 is the ethernet adapter which got the boot image from DHCP. 

On the LTSP server machine, eth0 is set to static IP for the DHCP server. Could that be part of the problem? Can someone offer suggestions?

---

