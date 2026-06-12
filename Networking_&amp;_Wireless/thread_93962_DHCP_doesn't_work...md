---
title: "DHCP doesn't work.."
date: 2005-11-23
forum: Networking &amp; Wireless
---

### Post by Sunnz on 2005-11-23
Here's the commands that I have used:

modprobe ath_pci
iwconfig ath0 essid "routerid"
iwconfig ath0 key XXXX-XXXX-XXXX-XXXX-XX enc open
iwconfig ath0 channel 12
iwconfig ath0 mode Managed
ifconfig ath0 up
dhcpcd ath0

But I couldn't get my IP and dhcpcd ath0 just turns off ath0... with no error messages...

---

### Post by Lambert on 2005-11-23
Instead of dhcpd ath0 try this command.

```
sudo dhclient ath0
```

---

