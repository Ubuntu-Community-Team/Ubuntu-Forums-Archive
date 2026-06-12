---
title: "Setting the default network card? (The on that gets the ip by dhclient on boot)"
date: 2005-05-27
forum: Networking &amp; Wireless
---

### Post by zith on 2005-05-27
Hello!

I recently changed from using my built in ethernet card in my laptop to using the integrated wireless network card. The problem is that every time I boot, ubuntu tries to initialize my ethernet card (eth1) while i want it to initialize my wireless network card (eht0). 

So the question is, how do I make ubuntu run something like "dhclient eht0" instead of "dhclient eth1" on boot?

---

### Post by f.prisson on 2005-05-27
Go to System -> Management -> Network disable DHCP for the old device and enable it for the new device.

---

### Post by zith on 2005-05-27
[QUOTE=f.prisson]Go to System -> Management -> Network disable DHCP for the old device and enable it for the new device.[/QUOTE]
 Thanks!

---

