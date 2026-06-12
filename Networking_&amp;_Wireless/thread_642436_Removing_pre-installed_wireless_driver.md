---
title: "Removing pre-installed wireless driver"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by julianmh on 2007-12-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/152522](https://bugs.launchpad.net/ubuntu/+bug/152522) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have the Realtek RTL8185 wireless card. I need to uninstall the pre-installed driver so that I can use the card with ndiswrapper. How would I do this?

---

### Post by kevdog on 2007-12-16
I dont think the module is loading at boot, although the module is preinstalled.  Check your /etc/modprobe.d/blacklist file.  If the r818x driver is blacklisted, its definitely not loading at boot and you can go ahead.

---

