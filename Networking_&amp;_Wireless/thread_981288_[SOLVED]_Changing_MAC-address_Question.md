---
title: "[SOLVED] Changing MAC-address Question"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by mr.propre on 2008-11-13
Hi

It's a little embarrassing asking this question after working almost 2 years with Linux but if I change my MAC-address in a terminal using the command: "ifconfig [interface name] hw ether [new MAC address]"

Will this change my MAC-address permanently or will it be back the old one as soon as I reboot ubuntu?

---

### Post by jongkind on 2008-11-13
Your command will not be permanent.
To tackle this I used macchanger (it is in the repositories). You can start it via /etc/rc.local. E.g you can put the command below in /etc/rc.local (just above exit), make the file executable, it will run for all users on boot.

macchanger -m 00:00:00:00:00:00 wlan0

The 'zeros' represent your mac address, wlan0 is in this case a wireless card.

---

### Post by mr.propre on 2008-11-13
Thanks, for the information :KS

---

