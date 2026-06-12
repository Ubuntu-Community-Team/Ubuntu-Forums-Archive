---
title: "D-Link PCI DWL-G510 v3 easy set up but needs restart every boot-up"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by Orvar on 2008-02-05
Hi! Can anyone help me? I use Ubuntu 7.10.
I´ve got a D-Link DWL-G510 wlan. Installing was no problem. Copied driver directory  from CD to my "downloads" directory, installed ndisgtk, opened "Wndows Wireless Drivers", installed NetRt61G.INF, and made the usual WEP setup in the network utility (all graphical, no Terminal commands).
After settin SSID, password and choosing DHCP it just worked. Fine. To "make sure" that it would work after re-boot I opened Terminal, wrote "gksudo gedit /etc/modules" and when opened I put "ndiswrapper" (without quotation marks, of course) at the end of the file. Saved and closed. Re-opened to check that it was still there. It was. Closed and re-booted.
Now:
No Internet connection. There are packages sent to the wlan, but no received.

However, if I open the wireless setup again, check Roaming, then OK, wait for a second or two, open it again and uncheck Roaming so that my normal WEP/DHCP turns on again -- "changing interface configuration" (or something like that, I have a swedish Ubuntu) flashes for a second, and everything works!!! 
(I get identical result if I change the setup to static IP, put in a false one which doesn´t work, say OK, open again and change back to DHCP. As soon as I change from "anything else" to DHCP the wlan starts working. But not from a fresh boot-up.

Of course, I could do this after every boot-up, but I would prefer if someone could help me on this issue. 
So my question is: What do I do to make the wlan work from start, without having to manually leave and then re-start my WEP/DHCP session?

---

