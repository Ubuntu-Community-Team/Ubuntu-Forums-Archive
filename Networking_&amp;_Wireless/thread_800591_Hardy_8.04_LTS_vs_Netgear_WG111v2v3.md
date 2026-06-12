---
title: "Hardy 8.04 LTS vs Netgear WG111v2/v3"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by led-bloon on 2008-05-20
Has anyone managed to get either the v2 or v3 dongle working with WPA (and hidden SSID)???

Feisty and Gutsy both work (reasonably) ok, with each dongle using ndiswrapper and the appropriate windoze drivers, but no luck at all with Hardy!!!
Hardy can connect with no encryption ok. Have not tried WEP, for obvious reasons.

Using v3 dongle and WPA-PSK/TKIP/TKIP settings:
wpa_supplicant, with "-d" debug, shows that Hardy fails mainly at 4-WAY handshake and occasionally gets past this, then fails at GROUP handshake. The key I am using is correct!

PS BIG thnx to Kevdog for his manual configuration post, used initially.
Now mainly using wicd (however in Hardy, wicd "locks up" frequently!!).:confused:

---

