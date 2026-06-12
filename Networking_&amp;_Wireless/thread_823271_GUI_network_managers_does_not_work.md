---
title: "GUI network managers does not work"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by museworry on 2008-06-09
Hello. I am having problems with conneting to wifi networks using managers.

For example, Network Montitor 2.12.1; My wifi has eth0 interface. And if I go to Network Monitor->Properties->Configure (eth0) it says 'The interface does not exist. Check that it is correctly typed and that it is correctly supported by your system.' Almost the same for KNetworkManager.

but i can easly connect in console:
```
sudo iwlist scan
sudo iwconfig eth0 essid XXX
sudo dhclient

```

this is my network settings:
```
 $  cat /etc/network/interfaces
auto lo eth0
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
```



What can be my problem?

---

