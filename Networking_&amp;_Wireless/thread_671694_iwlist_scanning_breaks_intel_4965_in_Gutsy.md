---
title: "iwlist scanning breaks intel 4965 in Gutsy"
date: 2008-01-18
forum: Networking &amp; Wireless
---

### Post by julianweber on 2008-01-18
I have a Dell  Inspiron E1705/9400 with the Intel 4965 wireless card running Gutsy 64bit.  I just recently upgraded the wireless card from a previous 3945 and also upgraded my wireless router to a Buffalo Wzr2-G300N.  I have booted windows and confirmed that I can connect at 130Mbps 802.11N but when I am in Ubuntu it will only show a connection at 802.11G.  It appears to work OK and I can mount drives via NFS and surf the web.  However, if I run iwlist scanning while the connection is up and working it will return the error, "wlan0     Failed to read scan data : Resource temporarily unavailable" and the wireless will no longer work.  I have tried using the Knetwork manager and reestablishing a connection but it won't work.  I have also tried connecting using wpasupplicant and it also will not connect.  A reboot however will bring everything back.  Does anyone have any suggestions where to start troubleshooting this?

---

