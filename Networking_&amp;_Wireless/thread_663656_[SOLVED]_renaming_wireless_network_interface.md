---
title: "[SOLVED] renaming wireless network interface"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by tr333 on 2008-01-10
How can I rename the wireless network interface?  It is currently set to 'wlan0_rename' (ubuntu default) and I would like to rename it to just 'wlan0'.  ifconfig seems to have problems displaying the whole interface name and just shows 'wlan0_ren' instead of 'wlan0_rename' which causes problems for scripts that parse the output of ifconfig.

Eg.  ACPI suspend script for network interfaces (/etc/acpi/suspend.d/55-down-interfaces.sh) reads in the interface name from the output of ifconfig, but can't actually shut down the interface because it has the incomplete name for the interface.

---

### Post by Digger78 on 2008-01-10
In feisty IIRC you can change it in **/etc/iftab**

In Gutsy you can change it in **/etc/udev/rules.d/70-persistent-net.rules**

---

### Post by tr333 on 2008-01-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/180766](https://bugs.launchpad.net/ubuntu/+bug/180766) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Thanks for the tip.  I solved my problem by deleting that file (/etc/udev/rules.d/70-net-persistent.rules) and rebooting the system.  This seemed to recreate my network interfaces.  Doing this seemed to create yet another network interface called 'wmaster0' though :?.

---

