---
title: "[SOLVED] Connecting problems"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by tad1073 on 2008-01-23
I am using madwifi-0.9.3.3 w/ network manager and key ring manager to remember my network and wep key. the problem is that i have to login in about 2 or 3 times before i am able to stay connected. On the first try it will try and connect then the window with the encryption type and passphrase or key pops up, i enter the info and get a connection then the connection drops and I have to click on the network icon>connect to other network and so on and so forth. Usually after the third time i am able to stay connected. Any ideas on this issue? Also there are entries on firestarter for ath0 and wifi0 were wifi0 is the actual connection.

Is there any way i can improve my signal strength, the router is on the first floor in the middle of the house and I am on the second floor at the west end of the house , about 12 ft. up and 35 ft. over.

---

### Post by tad1073 on 2008-01-24
bump... anyone

---

### Post by hahahan on 2008-01-24
You already might have tried to reposition your router and pc a little, keep all metal as far as possible from the antenna's,high freq. waves behave odd sometimes and a few inches could make a lot of difference. I believe there is nothing to improve at the pci wificard since the antenna's are inside. Mounting better atenna's to the router could improve your situation. Some wificards supports "iwconfig NIC txpower xx" (check man iwconfig) for adjusting the txpower but most likely it's max at default.

Hopes beeing helpfull.

---

