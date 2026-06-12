---
title: "reset nm-applet"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by mthode on 2007-04-25
It there anyway to reset all the information that nm-applet seems to have gathered.  I have changed the name of my ap and turned off ssid broadcast and it still shows up as the old name in nm-applet.

---

### Post by Buffalo Soldier on 2007-04-25
Maybe this bit infor can help. Run:```
gconf-editor
```
There's a list of AP's that you've connected in /system/networking/wireless/networks/

Not sure whether deleting the info there will reset nm-applet settings or not.

---

### Post by holihue on 2007-09-15
try: 
[https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-b651559fa3b43d055bfda1c52d9b7966938a204e](https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-b651559fa3b43d055bfda1c52d9b7966938a204e)


Try to edit the /etc/network/interfaces.

And remove the static ips.
it should look like only auto eth0(also eth1).
It worked for me:)

---

