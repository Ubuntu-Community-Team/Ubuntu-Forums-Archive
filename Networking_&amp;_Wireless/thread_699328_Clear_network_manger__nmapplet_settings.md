---
title: "Clear network manger / nmapplet settings"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by mattydee on 2008-02-17
Hi,

It seems nm-applet has decided it likes to have IP 192.168.1.103 on my home network. While this is not bad, I would prefer it to take 192.168.1.101. Is there a way to fix this behavior? 

The router is usually in charge of assigning IPs (through DHCP). In Ubuntu (as opposed to Slackware), the network manager seems to request the 192.168.1.103 and the router allows it. Clearing the settings in the router doesn't help, so ubuntu mist be doing something here...

---

### Post by spd106 on 2008-02-18
I believe you want to look in the /var/lib/dhcp3/ folder for *-leases files. This is where dhclient stores the most recent lease settings.

If there are more than one then it's probably best to just delete them all, bearing in mind that you will need sudo access to delete system files.

This should reset the lease request.

---

### Post by mattydee on 2008-02-25
That is EXACTLY what I was looking for. Thank you!!!
:guitar:

---

