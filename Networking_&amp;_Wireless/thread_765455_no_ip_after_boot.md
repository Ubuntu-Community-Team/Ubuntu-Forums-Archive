---
title: "no ip after boot"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by nohu_ on 2008-04-24
hi guys

i've got a problem with networking.
whenever i boot the computer (hardy) or resume from hibernation i've got no ip assigned to the Network interface eth0

The command ```
sudo dhclient eth0
``` solves the problem and i get an ip assigned
i couldn't determine the reason why my system started to behave like this.
I had Hardy Beta installed as the Problem started, but it didn't get better not even with the final release of hardy (today).

Any ideas? Wich daemon is starting DHCP-Lookup on boot-time normaly?
All other Workstations in the LAN have an ip after booting

Thanks and Cheers

---

### Post by Iowan on 2008-04-24
I haven't upgraded to Hardy yet, but...
Check the **/etc/network/interfaces** file to verify an "auto" line for eth0.

---

### Post by nohu_ on 2008-04-25
added auto eth0 to /etc/network/interfaces solved the prblem!

Cheers nohu_

---

