---
title: "troubles with hardware modem"
date: 2005-08-17
forum: Networking &amp; Wireless
---

### Post by Sai on 2005-08-17
i have hardware external modem Zyxel Omni Neo 56k connected to ttyS1 (com2 in win). All operation systems (windows all versions, freebsd 5.3, madrake linux) are working fine with it, but ubuntu doesn't. Ubuntu sometimes can detect it automatically (via pppconfig or "Network Settings") but not always. When ubuntu detects modem or i point ttyS1 manually and try to dial to provider - nothing happens. There aren't any sound (nor click, nor dialtone) in modem. After some time Ubuntu gives up.
Also there is a problem: after ubuntu used modem, it (modem) stops working under windows and i need to power off it to reset.
Maybe i need some drivers? Or i need to tune some settings?

---

### Post by Sai on 2005-08-22
Problem solved. chat-scripts from pppconfig were incorrect (maybe just for my system), so i tried gnome-ppp and it began to work with modem correctly.

---

