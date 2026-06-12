---
title: "how to setup wireless (with WPA-PSK) in console"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by fhqwhgad on 2007-12-21
Hi,
I need to setup my wireless network when i'm in console (before i startup X), but i have not been able to succeed. I have an intel 2915ABG in it, and it is a hidden wifi network with WPA-PSK encryption.

I know everything works. If i startup X and let network-manager set it all up, it works fine. I guess i just can't figure out how to configure it manually in console.

I've tried various iwconfig eth1 commands and various attempts to write in the /etc/network/interfaces, still with little success.

How do i get this to work? If you need more info, ask away.

---

### Post by spd106 on 2007-12-22
The Howto Wireless Security sticky linked on page 1 should provide most of the information you need. 

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by fhqwhgad on 2007-12-23
> **spd106 said:**
> The Howto Wireless Security sticky linked on page 1 should provide most of the information you need. 

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

I have tried setting it up like that, but when i restart the network interface it says No DHCPOFFERS received.

My /etc/network/interfaces looks like this:
auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-ssid myap
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk alonghexkey

---

