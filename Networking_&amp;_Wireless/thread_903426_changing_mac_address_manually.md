---
title: "changing mac address manually"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by dexter.deepak on 2008-08-28
i am currently using macchanger to fake my wireless mac address. i want to do this manually.
i had been through many webpages and all of them explain setting the eth0 interface...but i want something for the wlan0 interface.
PLUS i am looking for a permanent setting for this..at present i have to set the address everytime i start my pc.

i followed this link:
[http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/)
this holds the following code :
```
auto eth0
iface eth0 inet dhcp
       hwaddress ether 01:02:03:04:05:06
```
i have replaced eth0 -> wlan0 ; but what about ether ?

i would like to mention, that my /etc/network/interfaces file consistes ONLY loopback entries, and not anything for wlan or eth interface :
```
auto lo
iface lo inet loopback
```

---

