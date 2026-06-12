---
title: "wifi radar won't connect - iwconfig does ???"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by glenn69 on 2007-02-06
I am trying to connect to wireless network with WEP configured.

I have set the appropriate values in wifi radar ex..WEP key, ssid, etc.. and it will not connect.

If I enter in a terminal :
sudo iwconfig eth0 esid "myessid"
sudo iwconfig eth0 key "my key"

then the connection will be made.

Why? and what can I do to have it connect automatically?

---

### Post by etienne.navarro on 2007-02-07
Try using Network Manager. If using Gnome install network-manager-gnome, or KDE knetworkmanager.

---

### Post by sethjvm on 2007-02-07
Are you broadcasting your SSID name?

---

