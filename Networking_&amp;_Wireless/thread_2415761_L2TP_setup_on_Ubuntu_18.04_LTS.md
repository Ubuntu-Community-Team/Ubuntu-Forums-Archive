---
title: "L2TP setup on Ubuntu 18.04 LTS"
date: 2019-03-31
forum: Networking &amp; Wireless
---

### Post by iamtesting on 2019-03-31
Hi. im trying to setup L2TP vpn on Ubuntu 18.04. i have already installed network-manager-l2tp. and the l2tp option does show up when i click on add new connection. when i click on add new connection, i get a menu. and this is where im stuck. i dont know what should i type in there. these are the info provided by my vpn provider

-Ipsec pre-shared key
-username and password
-server address
Edit : this is the menu i get : [http://pasteall.org/pic/4a47d642a05f59a32071ef3038bf9614](http://pasteall.org/pic/4a47d642a05f59a32071ef3038bf9614)

---

### Post by dkosovic on 2019-04-03
Here are the mappings from what your VPN provider provides to what NetworkManager-l2tp has:

[LIST]
[*]Server Address : Gateway
[*]username and password : same.
[*]IPsec pre-shared key : same (find it in the IPsec Settings where you'll also need to enable IPsec).
[/LIST]

Referring to the package's README.md file :
   [https://github.com/nm-l2tp/NetworkManager-l2tp/blob/1.2.10/README.md](https://github.com/nm-l2tp/NetworkManager-l2tp/blob/1.2.10/README.md)
under the *"Issue with not stopping system xl2tpd service"* section, you might need to stop the system xl2tpd service.

Also see the *"Issue with VPN servers only proposing IPsec IKEv1 weak legacy algorithms"* section, you might need to fill in the Phase 1 & 2 Algorithms if your VPN provider is using weak legacy algorithms.

---

