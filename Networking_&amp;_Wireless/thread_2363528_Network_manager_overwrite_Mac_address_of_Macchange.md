---
title: "Network manager overwrite Mac address of Macchanger"
date: 2017-06-11
forum: Networking &amp; Wireless
---

### Post by joan_carles2 on 2017-06-11
I want to use macchanger to modify the macaddress each time I restart the computer.

I did it and works, but the problem is that after using macchanger... Network manager revert the values given by macchanger. So macchanger changes the Mac Address and Network-manager write it again leaving the original Mac Address-

To solve this I tried to modify the config file of Network Manager (/etc/NetworkManager/Networkmanager.conf)

```
[device]
wifi.scan-rand-mac-address=no


[connection]
ethernet.cloned-mac-address=preserve
wifi.cloned-mac-address=preserve

```

After this I restart the computer and nothing happens. I'm using lubuntu 16.10 and the network manager version is 1.2.6.

Any solution to work out my problem

---

### Post by d0006 on 2017-10-07
Bump

---

