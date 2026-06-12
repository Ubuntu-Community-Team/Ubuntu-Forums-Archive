---
title: "Networking broken after upgrade to linux 2.6.24.-21"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by irotas on 2008-10-28
This morning I upgraded to linux 2.6.24-21 because of the 'security update' available the Update Manager. Unfortunately, immediately after rebooting my networking is no longer working.

If I type 'ifconfig', only 'lo' is shown - 'eth0' is now gone. The icon for the 'Network Manager' applet has a little '!' on it and says "No network connection" when I hover the mouse over it.

However, if I type 'dhclient eth0', 'eth0' comes right back up and even gets an IP address.

Perhaps the only thing "special" about my installation is that I'm running from within VMWare with "Bridged" networking. This has always worked in the past, even through several updates of the Linux kernel, but today it's busted.

Is anyone else having similar problems?

-Adam

---

### Post by irotas on 2008-10-28
So I modified my 'Wired Connection' in the Network Manager applet and unchecked 'Enable roaming mode' and set 'Configuration' to DHCP.

Now if I reboot the network interface comes up, gets an IP address, and is able to communicate on the network.

However, the Network Manager icon still has a '!' and says 'No network connection' when I hover the mouse over it. Strange!

---

### Post by irotas on 2008-10-28
I have submit a bug report here:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/290290](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/290290)

---

