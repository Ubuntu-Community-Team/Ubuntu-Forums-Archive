---
title: "Internet connection is dead"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by TheSixthPandava on 2008-11-01
I have a problem with my cable internet connection. I had a problem with Transmission [in case of reboot without proper closing of Transmission, it didn't remember torrents it downloaded but went back to 0,0%: this problem still exist, I guess], and I tried to fix it, and I wanted to check if I did. I rebooted computer while Transmission was working and after that reboot, my connection went completely dead [modem is recognized and connected, I can see that, but I can't open any webpage and do anything with connection]. 

Since I haven't seen anything I did that could cause this behaviour, I called Technical Support of my cable provider, but they said it is all OK with them, and it seems that they are right, because after I booted from Ubuntu Live CD, internet is working as normal.

Does anybody have any idea what is happening or had similar problem?

---

### Post by dburnett77 on 2008-11-01
Most likely while your modem/router was set in uPNP mode, someone reconfigured your firewall settings.

Typical attacks include Ping of Death, firewall lock (host undefined), and closing all ports.

You could try purging your firewall next time, and re-installing.

---

### Post by TheSixthPandava on 2008-11-01
YES! That was it! You solved my problem! Thanks!

---

