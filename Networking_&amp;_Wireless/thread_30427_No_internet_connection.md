---
title: "No internet connection"
date: 2005-04-28
forum: Networking &amp; Wireless
---

### Post by Masai05 on 2005-04-28
I'm a total newbie to this linux thing.  I tried the live cd and everything worked perfectlyin including the cable internet.  Once I installed the software everything worked but the cable internet connection.  I didn't have the cable plugged in during installation, any suggestions how to remedy this?

---

### Post by alastair on 2005-04-28
When you say "cable" - do you mean some sort of modem? USB or ethernet?

If there's a specific network device to access - check the system logs and see if you can see the device getting probed/found at boot :

/var/log/syslog

If it is a PPPoE type config, and your device is recognised, try : pppoeconfig

---

### Post by nad on 2005-04-28
As ubuntu did not get a reply from a dhcp server when it was installed, your network configuration is not completed.

Use the network configuration tool in the System Configuration menu with the cable plugged in. Highlight eth0 and click properties. Under Connections choose the Automatic (DHCP) option and ok out of the menus.

---

