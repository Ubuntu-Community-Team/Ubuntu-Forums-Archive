---
title: "Connecting to a Campus  Wireless Network (7.10 Studio)"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by SL1210 on 2007-11-10
I´ve been able to connect to all wireless networks except my schools (Purdue University, I figured I´d say the name so other students would be able to search). When I searched I found other students having this problem, but from different universities. Here are the requirements for connecting:


Network Name: PAL2.0
Wireless Security: WPA Enterprise
EAP Method: PEAP
Key Type: TKIP
Phase2 Type: MSCHAPV2
Identity: Your Purdue Login
Password: Your Purdue Password
Anonymous Identity: (leave blank)
Client Certificate File: (None)
CA Certificate File: Click it, then enter:
      Location: /etc/ssl/certs/Thawte_Premium_Server_Ca.pem
      Alternatively: /usr/share/ca-certificates/mozilla/Thawte_Premium_Server_CA.crt 
Private Key File: (None)
Private Key Password: (leave blank)

I´m running Ubuntu Studio 7.10 with Gnome, and I can´t figure out how to setup that connection in the network administration program.  It has wireless DHCP and Wired .... but I don´t see where I can make a new location with these settings (let alone save them so I don´t have to enter them every time I want to connect).

Any help would be appreciated!

Kind Regards,
-Chad

---

### Post by SL1210 on 2007-11-11
Anyone?

---

### Post by Whiffle on 2007-11-11
Right click the little network icon on your taskbar, click "other wireless network", and then you should be able to enter all that information in.

---

### Post by tubasoldier on 2007-11-11
If you are not using NetworkManager you could also give WifiRadar a shot. It will find all available wireless networks, and you chould be able to connect that way. I used to use it all the time. I'm not sure about Perdue, but at my college we simply connect to the network and then veryify your login information in a web browser after your connected. And I always pass the security check with flying colors, even with no antivirus.

---

### Post by rodsoto12 on 2008-06-16
what do I need to connect my wireless card, so I can get wireless internet?

---

