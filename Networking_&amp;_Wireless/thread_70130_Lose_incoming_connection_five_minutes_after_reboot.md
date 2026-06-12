---
title: "Lose incoming connection five minutes after reboot"
date: 2005-09-29
forum: Networking &amp; Wireless
---

### Post by chiok on 2005-09-29
Howdy.

I just switched routers (from SMC 7004VBR-CA to Belkin F5D7230-4).  With the SMC router, I only had one IP address for every computer on my lan.  Networking didn't take any setup on my part to work.  With the Belkin, each computer has a separate IP address and the networking works for the first five minutes after a reboot since I ran pppoeconf.  The DSL modem is a Bell Sympatico issued Speedstream 5200.

The network now works fine for the first five minutes, but I can't get anything incoming (e.g, ping, firefox, apt-get) after that.  However, I can still see an apache2 webpage from another computer on the network.

Any ideas?  Thanks.

---

### Post by chiok on 2005-10-01
I found a hack to fix this problem.  Comment out make_resolv_conf() in /etc/dhcp3/dhclient-script.

[http://ubuntuforums.org/archive/index.php/t-24093.html](http://ubuntuforums.org/archive/index.php/t-24093.html)

---

