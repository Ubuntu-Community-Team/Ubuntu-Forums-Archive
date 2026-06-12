---
title: "Wired no IP renew when idle? [15.04]"
date: 2015-07-17
forum: Networking &amp; Wireless
---

### Post by luciano.x on 2015-07-17
eth0 seems to be in trouble to renew IP but only when I don't use network for a while like 1/2 hour. When resuming from suspend/blank screen network is OK.
For me it seems that there's some kind of timeout. Need help to fix.

So I did [FONT=times new roman]$ sudo ifconfig[/FONT] and it shows no ip assigned to eth0.

*Fix: click network icon -> wired connection. Notification appears "connected to wired connection" and everything back to normal. PS: wired is ON*

I assume [FONT=times new roman]$ sudo dhclient[/FONT] [FONT=times new roman]eth0[/FONT] would work as well.
Thoughts on this?

+Info: 
my SO is in another lang. Notifications/menus may be different.
laptop dell
wireless is off
network settings is default
...something else I didn't mention?

---

### Post by luciano.x on 2015-07-28
Ok looks like I solved with the following workaround:
DHCP lease time in my router set to 86400 secs (it was 3600).

---

