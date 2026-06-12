---
title: "vlan user authentication"
date: 2017-01-02
forum: Networking &amp; Wireless
---

### Post by fecheval on 2017-01-02
ive been giving a username and password for a vlan (openvpn). ive gone through many suggestions that i can google but no luck on configuring ubuntu 16.04 to connect to it. I can connect via a cell phone though no problem. any suggestions on how i can connect without having certs, i just have a user and pass.

---

### Post by TheFu on 2017-01-02
Welcome to the forums.

The admin should have provided an .ovpn file which contains the client-side settings needed to connect.

I suspect it isn't to authenticate to a VLAN, but perhaps to a network?

---

### Post by fecheval on 2017-01-02
no sorry, only thing that is needed to authenticate to the vpn, not network is. ip or dns name, username ,  password.  works in other os's fine, but when i try to add a vpn through the gui there isnt an openvpn option that allows to to connect w/o certificate.

---

### Post by TheFu on 2017-01-02
> **fecheval said:**
> no sorry, only thing that is needed to authenticate to the vpn, not network is. ip or dns name, username ,  password.  works in other os's fine, but when i try to add a vpn through the gui there isnt an openvpn option that allows to to connect w/o certificate.

I've never used a GUI to make an openvpn connection.  
To my knowledge, the .ovpn file must have similar lines to:
```
ca ca.crt
crl-verify crl.pem
```
These lines points to the provided x509 cert and the CA which signed it (those files are in the same directory, so no path is needed). userid + password is something that is also required.

To my knowledge.

---

