---
title: "I cannot connect to 802.1x EAP Wifi Network"
date: 2019-02-05
forum: Networking &amp; Wireless
---

### Post by nitrucks on 2019-02-05
As title states, I cannot connect to the 802.1x EAP netwrok my school provides to it's students. It reqires the username and password given to us, which i have.

I am using Lubuntu but when i click on the network SSID in WiFi networks, the connection doesnt prompt anything, there is no username or password box, no asking for just a password, it simply closes and nothing happens.

I tried updating network manager and trying to create a new connection from scratch but I have not been able to connect.

Thank you for you time and help!

---

### Post by pcfan1234 on 2019-02-05
Try to create a wireless network manually. Manually type the SSID (Name of the Network).
Then select under the settings section the method Dynamic WEP (802.1x). There you can enter you credentials.

---

### Post by nitrucks on 2019-02-06
I have tried this before, but the network manager says that dynamic wep is not currently supported. I have updated and upgraded the system as a whole, so I am not sure how to update any further...

---

### Post by pcfan1234 on 2019-02-06
In a fresh installed version of 18.04 it works out of the box.
Try using nmcli: [https://major.io/2016/05/03/802-1x-networkmanager-using-nmcli/](https://major.io/2016/05/03/802-1x-networkmanager-using-nmcli/)

---

