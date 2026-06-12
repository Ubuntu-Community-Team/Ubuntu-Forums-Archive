---
title: "acx111 won't connect"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by scatyb on 2006-09-16
well, about 3 days ago I finally got my wireless to work.  How?  I don't know.  I installed kismet and a couple other networking tool and magically it worked.  However, stupid me had to install the dapper updates today and now my wireless no longer connects.  It's on dhcp, I can find a signal via iwconfig but it will not get an IP.  I tried manually configuring it, but nothing.  something I'm missing?

---

### Post by scatyb on 2006-09-16
nevermind, I got it to work, a little rinky dink though.

It seems I stumbled upon the last way I got it to work.

Here it is in all it's simplistic glory.


remove network-manager / netwag / netwox

reboot

reinstall network-manager/netwag/netwox

Deactivate wlan0

reboot

Set ESSID

deactivate

iwlist scan

sudo ifup wlan0


works like a charm now.

---

