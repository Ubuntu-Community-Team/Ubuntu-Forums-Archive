---
title: "Connecting to a specific AP"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by thrillhouse on 2007-07-03
Is there a way to easily connect to a specific access point if there are two with the same SSID?  The network manager applet just lists one of them but iwlist will give all of them in the area.  Thanks.

---

### Post by spd106 on 2007-07-03
As far as I am aware this is possible. but it involves editing a key the gconf registry. The steps are outlined in this wiki page, simply put in the bssid of the AP that want to connect to and remove the others. Then NM should attempt to connect to that AP first.
[https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-d2b310228dc887b6cddf4465b6a53cdc4dc9be28](https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-d2b310228dc887b6cddf4465b6a53cdc4dc9be28)

---

