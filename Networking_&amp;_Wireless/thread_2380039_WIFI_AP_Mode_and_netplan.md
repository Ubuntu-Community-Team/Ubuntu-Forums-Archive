---
title: "WIFI AP Mode and netplan?"
date: 2017-12-12
forum: Networking &amp; Wireless
---

### Post by bern1 on 2017-12-12
Hi, 
Please advice me how to prepare netplan file for wifi AP mode. 
I have newest ubuntu server 17.10 and use networkd. 
See my network settings details:
[http://paste.ubuntu.com/26177281/](http://paste.ubuntu.com/26177281/)

I installed hostapd and made hostapd.conf file but wifi AP doesn't work.
Maybe netplan does not support networkd and ap mode?
If not how could I start configuration in different way?

[NetPlan documentation]("http://manpages.ubuntu.com/manpages/artful/man5/netplan.5.html") (I do not know if it's up to date) says that:
> ap  is  only  supported                      with NetworkManager.
TIA

---

### Post by bern1 on 2017-12-17
Alhough this is wifi interface I set 'ethernets' in the netplan file:
```
network:
  version: 2
  renderer: networkd
  ethernets:
    wlp4s0:
      addresses:
       - 192.168.1.1/24
      dhcp4: no
```
and wifi wlp4s0 interface receive static address 192.168.1.1 and works OK.

---

