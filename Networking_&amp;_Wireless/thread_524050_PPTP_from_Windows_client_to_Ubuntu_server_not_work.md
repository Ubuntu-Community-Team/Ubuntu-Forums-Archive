---
title: "PPTP from Windows client to Ubuntu server not working."
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by OpticalIllusion on 2007-08-12
I installed PoPToP and Webmin and configured a PPTP server so that I can VPN from my Windows XP laptop to my Ubuntu home server.  I got it working to the point that I can login and connect to the VPN, but once I'm in, I cannot browse the internet or anything.  I've tried a few different PPP Options settings in Webmin, but no luck so far.  I am using all default encryption and security settings on the server options and on the Windows client settings.

---

### Post by OpticalIllusion on 2007-08-12
Ah, I guess in the Windows client options I had to uncheck "Use default gateway on remote network" to make it work since I'm connected to my LAN.  I didn't have to do that when connecting from Windows client to Windows VPN server.  It's still pretty slow, but I'll keep messing with it.  If anyone has experience, please share your settings with me.

---

