---
title: "Wifi connection drops after 17.04 upgrade"
date: 2017-05-20
forum: Networking &amp; Wireless
---

### Post by sergth on 2017-05-20
Hi, i have upgraded my Lubuntu to 17.04 and I have trouble with connection.
I have virtualized (Virthalbox) Lubuntu.
I use one wifi AP, which has a pretty bad signal (somewhere between -75 and -80 db), but working fine.
Well, till this update. At 16.10 I was able to connect with no problem, althrough the signal is bad. Now on 17.04, it will not connect me at all. it Asks me for password, it spins a connection icon for a while and then tells me I am disconnected.

It is probably a linux problem, because VBox has no change on it, and if I shut down my virtualized machine an try to connect on windows, I will get connected.

And I use TP-Link TL-WN722N which uses ath9k drver. Driver I have installed through repository, I do not remember the package name, but it was some kind of universal driver bundle, so I think this is still up to date, maybe upgraded with distribution.

I have also tried to go through some guides and ideas, trying to play with TXpower, or specifying BSSID MAC to saved network (as someone said it tries to reconnect to nome neighboured network aka roaming), I have also tried to find some connection trusthold somewhere in system, or just turning off the power management, but nothing was successful.

I really dont want to reinstall whole system back to 16.10, so please, someone any ideas why on 17.04 I cannot connect?

Thanks :)

---

### Post by jeremy31 on 2017-05-20
Try
```
sudo -H gedit /etc/NetworkManager/NetworkManager.conf
```
Add
```
[device]
wifi.scan-rand-mac-address=no
```
Then
```
systemctl restart network-manager.service
```

---

### Post by sergth on 2017-05-20
Works like charm.
Thank you a lot man ;)

---

### Post by jeremy31 on 2017-05-20
I guess I should have said Welcome to the forums

Please use the thread tools menu near the top right of the page to mark as solved

---

### Post by sergth on 2017-05-20
Of course :) And thanks again :)

---

