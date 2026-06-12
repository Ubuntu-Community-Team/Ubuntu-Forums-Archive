---
title: "pppoeconf broke my network manager"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by maerlin on 2008-06-07
I guys,
I need your help, I've already looked in the forum for a solution but without luck.

Friday I ran pppoeconf because I needed to set up a pppoe connection.
The issue is that since then I haven't been able to use my wireless card again :/

I don't know why, but now the network manager doesn't recognise any wireless network. I tried to reinstall it but no luck.
Clicking on it I see only "wired connection", "modem connection", "manual configuration" and "something 802.1X"... no wireless options :/

The wireless card is working fine (with sudo iwlist wlan0 scan I can see my wireless network), how can I fix the network manager?

Please don't tell me to install another tool, the NM was running really fine, I only want to get it works again.

Thanks to all in advance

---

### Post by maerlin on 2008-06-08
Any idea?

---

### Post by maerlin on 2008-06-08
Just for information, I fixed it simply deleting /etc/network/interfaces .
After a reboot the network manager worked fine again.

---

