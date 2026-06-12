---
title: "problem with VPN and Internet connection"
date: 2019-01-01
forum: Networking &amp; Wireless
---

### Post by metal75 on 2019-01-01
hello guys.i had ubunto 17 and have some problems.when i connect to PPTP VPN everythings is ok.but when i disconnecting vpn i cant surf the web and i must disconnect wireless and connect again to surfing web,yesterday i upgraded to Ubunto 18.04 But the problem exist. please help me guys

Thank you.

---

### Post by clementc on 2019-01-01
Hi [**[COLOR=#000000]metal75[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115236"),

Can you please take the following steps and advise if this has helped resolve your issue:

1. In Terminal (press Ctrl + Alt + T to open), type: sudo nano /etc/NetworkManager/NetworkManager.conf
2. At the bottom of the file, add: dns=dnsmasq
3. Press Ctrl + X, then Y and Enter to save the changes.
4. Restart NetworkManager by typing: sudo systemctl restart NetworkManager

---

