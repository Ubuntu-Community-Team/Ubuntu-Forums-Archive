---
title: "how to setup netplan using PMF / ieee80211w=2 option for WPA3 enterprise?"
date: 2024-11-07
forum: Networking &amp; Wireless
---

### Post by landjalan on 2024-11-07
Hi, 

I could connect to my companys WPA3 enterprise network with a manually created wpa_supplicant.conf. But when using NetworkManager/netplan I am at a loss how to enable PMF (protected management frames). In my wpa_supplicant.conf I can simply set "ieee80211w=2" which is an requirement for "key_mgmt=WPA-EAP-SHA256".

I figured out that in netplan I can set key_management: "eap-sha256" (which was key_mgmt=WPA-EAP-SHA256 in wpa_supplicant.conf) but I did not find anything regarding "ieee80211w=2" to enable PMF (protected
# management frames).

Can someone help me out please ?

---

### Post by landjalan on 2024-11-29
solution: one does not need any "ieee80211w or "PMF" setting in netplan. when using "eap-sha256" as key managemant netplan/Networkmanager obviously figures the need out on its own. i just setup certificates plus key (must have a password) and it works now:

> access-points:
        "wlan01":
          auth:
            key-management: "eap-sha256"
            method: "tls"
            identity: "markus.giese@sinc.de"
            ca-certificate: "/usr/local/rootca.pem"
            client-certificate: "/usr/local/usercert.pem"
            client-key: "/usr/local/usrcert/myprotectedkey.pem"
            client-key-password: "12345678"
          networkmanager:
            uuid: "any ID"
            name: "wlan01"

no passthrough options are necessary

---

