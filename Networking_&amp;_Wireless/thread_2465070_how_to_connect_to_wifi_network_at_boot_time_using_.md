---
title: "how to connect to wifi network at boot time using NetworkManager"
date: 2021-07-21
forum: Networking &amp; Wireless
---

### Post by tvs on 2021-07-21
I'm using Ubuntu 20.04 and, unless I log in, the server does not connect to the wifi network.

I've found a non-optimal solution/workaround using these steps:

[LIST=1]
[*] Stopping and disabling NetworkManager
[*] Establishing the connection using 'wpa_supplicant'
[*] Getting an IP with 'dhclient'
[/LIST]

but I couldn't figure out how to do this using NetworkManager, anyone knows how to connect to the wifi network at boot time using NetworkManager?

Any tip/suggestion would be much appreciated, thanks!

---

### Post by TheFu on 2021-07-22
Servers don't use network-manager. They use **netplan.io**.  Networking is brought up at boot, not login.

Don't use network-manager on a server.  [https://askubuntu.com/questions/1105069/how-to-enable-wireless-on-ubuntu-server-18-04-via-cli](https://askubuntu.com/questions/1105069/how-to-enable-wireless-on-ubuntu-server-18-04-via-cli) has an answer that uses netplan.

---

