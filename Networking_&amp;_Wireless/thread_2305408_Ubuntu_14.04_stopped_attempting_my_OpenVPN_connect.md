---
title: "Ubuntu 14.04 stopped attempting my OpenVPN connection ?"
date: 2015-12-05
forum: Networking &amp; Wireless
---

### Post by tom214 on 2015-12-05
I had installed OpenVPN and then used Network Connections to create a VPN connection from a VPN provider. Everything was working fine with the VPN for days. After my WiFi connection was established, I'd right-click on the network icon -> VPN Connections -> then select my VPN connection, then I would see it attempting to connect (the pulsating effect in the icon).

All of the sudden yesterday I tried connecting to my VPN and I can see it's making NO ATTEMPT to connect - the icon doesn't change at all (no pulsating), so nothing happens. I don't receive any "VPN connection failed" error. Also, on the network icon if I do "VPN Connections" -> "Configure VPN" nothing happens either. 

I checked the OpenVPN server connection by running start and status in the terminal - it appears to run fine. I thought I might have messed up OpenVPN or my VPNs keys and certs by accidentally restoring a folder from the trash, so I did a complete reinstall of OpenVPN, Easy-RSA and created a new VPN connection, but I still get the same results.

Any ideas?

---

### Post by tom214 on 2015-12-05
Whoops, not much of an issue after all. I simply needed to double-click on my VPN connection to get it to attempt. Single click worked before. Not sure why single click stopped working.

---

