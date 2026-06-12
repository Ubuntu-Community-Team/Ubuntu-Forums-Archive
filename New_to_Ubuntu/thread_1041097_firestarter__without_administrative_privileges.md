---
title: "firestarter  without administrative privileges"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by gridd on 2009-01-16
hi is there a how to enabling a second user to use firestarter without having administrative privileges.

Or is it running in the background even when i,m not logged in?

---

### Post by Hallvor on 2009-01-16
> **gridd said:**
> hi is there a how to enabling a second user to use firestarter without having administrative privileges.

Or is it running in the background even when i,m not logged in?

If I have understood it correctly, Firestarter is only a GUI for IPtables, the Ubuntu "firewall". IPtables will run even if Firestarter is shut down. By default all ports are open in IPtables.

---

### Post by blueridgedog on 2009-01-16
I may be wrong, but I suspect firestarter is just a graphical tool to configure iptables.  As such, the firewall will be configured and working while the non-administrative user is logged in, but he/she will not be able to use the tool to adjust the settings.

---

### Post by gridd on 2009-01-16
Ok, thank you for your fast replies people.

---

### Post by hyper_ch on 2009-01-16
why do you feel teh urge to bother with iptables/firewall anyway? This is not Windows that you are using...

---

### Post by blueridgedog on 2009-01-16
> **hyper_ch said:**
> why do you feel teh urge to bother with iptables/firewall anyway? This is not Windows that you are using...

In my time as a system admin, I have had plenty of troubles with Linux systems that were "owned" due to open services and a lack of a firewall.  They became open spam relays and sources

---

