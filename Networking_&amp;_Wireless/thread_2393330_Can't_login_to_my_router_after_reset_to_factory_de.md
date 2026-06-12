---
title: "Can't login to my router after reset to factory defaults"
date: 2018-06-01
forum: Networking &amp; Wireless
---

### Post by donsy on 2018-06-01
Out of an abundance of caution due to the VPN filter malware attack on routers, I not only rebooted my router but I also reset it to the factory defaults. But now I can't access the login screen via the 192.168.1.1 IP address. I either get a hard wait and a timeout or an immediate not found message. What I expected after the reset was to be able to access a default login screen where I enter admin/admin to access the router settings. I previously saved my configuration to a file and I planned on restoring my configuration after logging in. My router is a Linksys E900.

---

### Post by donsy on 2018-06-02
Solved: UFW was set to deny outgoing and the unsecured login port to the router wasn't allowed, so I temporarily disabled the firewall.

---

