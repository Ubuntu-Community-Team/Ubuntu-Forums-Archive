---
title: "netplan doesn't apply after reboot"
date: 2018-08-14
forum: Networking &amp; Wireless
---

### Post by jonathanese on 2018-08-14
To get straight to the point, I'm using Ubuntu Server 18 as my router, and any time I reboot the server, I have to run netplan apply before I can get any connection.

netplan apply was already in crontab by default to run at reboot, but it doesn't seem to apply anything.

Reading around, apparently there's something about devices not being named correctly at boot? Perhaps delayed execution of netplan apply would help?

---

