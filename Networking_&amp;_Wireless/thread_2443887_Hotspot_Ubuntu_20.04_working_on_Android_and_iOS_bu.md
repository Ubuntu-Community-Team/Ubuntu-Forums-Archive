---
title: "Hotspot Ubuntu 20.04 working on Android and iOS but not on Windows"
date: 2020-05-21
forum: Networking &amp; Wireless
---

### Post by marco-bruurs on 2020-05-21
Hello,

I created on Hotspot on my Ubuntu 20.04 (upgraded from 18.04) and this is working on any Android and iOS device.
On an Windows 10 device I am not able to connect. When connecting it sticks on checking network requirements. Other SSID from my router is working.
Someone an idea? 

/etc/NetworkManager/system-connections/Wi-Fi1.nmconnection                                                                [connection]
id=Wi-Fi1
uuid=46a52393-d37e-4689-b444-5efd79e554e0
type=wifi
permissions=


[wifi]
mac-address-blacklist=
mode=ap
ssid=<Intend to be empty>


[wifi-security]
key-mgmt=wpa-psk
psk=<Intend to be empty>


[ipv4]
dns-search=
method=shared


[ipv6]
addr-gen-mode=stable-privacy
dns-search=
ip6-privacy=0
method=shared


[proxy]

---

