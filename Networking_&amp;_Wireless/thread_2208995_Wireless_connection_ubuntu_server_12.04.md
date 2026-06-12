---
title: "Wireless connection ubuntu server 12.04"
date: 2014-03-03
forum: Networking &amp; Wireless
---

### Post by ole4 on 2014-03-03
Hi

I have a problem with ubuntu 12.04. I had tried to connect ubuntu to a WPA2 network.

In this file /etc/network/interfaces looks:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet dhcp


auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid ESSID
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-eap PEAP
wpa-key-mgmt WPA-EAP
wpa-identity username
wpa-password password
wpa-phase1 fast_provisioning=1
wpa-phase2 auth=MSCHAPV2
```


The settings in ubuntu gui looks:

Wireless security: WPA & WPA2 Enterprise
Authentication: Protected EAP (PEAP)
Anonymous identity: empty
CA certificate: (None)
PEAP version: Automatic
Username: [EMAIL="username@department.com"]username@department.com[/EMAIL]
Password: Password


And then ignore the certificate.

Please, is there some one who can help me?

Thanks
Oli

---

### Post by IvoGuerreiro on 2014-03-03
Hi, 
Read this, it can be enlightening.
```

http://ubuntuforums.org/showthread.php?t=571188

```

---

