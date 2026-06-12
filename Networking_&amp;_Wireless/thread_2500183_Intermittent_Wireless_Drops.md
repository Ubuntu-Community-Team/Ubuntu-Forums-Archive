---
title: "Intermittent Wireless Drops"
date: 2024-08-25
forum: Networking &amp; Wireless
---

### Post by srwilde2 on 2024-08-25
Hello,

wirelessinfo.txt: [https://paste.ubuntu.com/p/DWXpRm5RNn/](https://paste.ubuntu.com/p/DWXpRm5RNn/)

I'm trying to use an Ubuntu 24.04 LTS laptop as a mini home server.  The laptop intermittently stops accepting incoming connections (ports 443, 8080, 32400 - SSH, Web, Plex).  The server will work well for some short amount of time but will then stop working.  The issue occurs regardless of the client used (Macbook, iPad, etc.), leading me to believe it is an issue with the server or the Starlink router.  Rebooting the server or the client will restore connectivity for a short amount of time (several seconds to several hours).  127.0.0.1 always works.

Steps I've tried to troubleshoot:
1.  Ensured Powermode is set to 'Performance'
2.  Ensured the server is always on power, never just battery
3.  Tried with NordVPN on and off on both the server and client (local network is whitelisted) -- VPN seems to have no effect on the issue
4.  Set ../default-wifi-powersave-on.conf to 'wifi.powersave = 2'
5.  Ensured the server has good wireless access to the router (never more than 20' with no obstructions)

Thank you for the help.

---

### Post by currentshaft on 2024-08-25
If the laptop is going into suspend/hibernate, it should be pretty easy to determine that from the system logs. Have you checked those with something like "journalctl -b"?

---

