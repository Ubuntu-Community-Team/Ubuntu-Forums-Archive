---
title: "Dual booting: If I setup a static IP address in Win7 will my address in Ubuntu also.."
date: 2014-01-03
forum: Networking &amp; Wireless
---

### Post by geo488 on 2014-01-03
I am dual booting Windows and Ubuntu. If I change my IP address from DHCP to static in windows, will it be static in Ubuntu also? I ask because I've been trying to setup port forwarding using the website [http://portforward.com/](http://portforward.com/) but many of its steps are when using Windows. Thanks!

---

### Post by hoopia on 2014-01-03
Windows networking is different then Ubuntu, you have to set it up static in both locations (obviously the same IP address). In Ubuntu, you can go to your Network Connections, Edit->IPv4 settings, change the method to Manual (instead of Auto DHCP).

---

### Post by geo488 on 2014-01-03
In Ubuntu I did that but I'm not sure it did anything. Essentially I switched the method to manual then typed nm-tool and copied and pasted the info there to Network Connections and restarted my computer. Did that do it? Is there any way to verify it's done?

---

### Post by hoopia on 2014-01-03
You can verify it's complete by going into Terminal and typing in **ifconfig **and viewing the relevant network connection (usually it's wlan0 if wireless, or eth0 if wired).

It should display the correct IP address next to the line inet addr.

Example line from my output:
inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0

---

