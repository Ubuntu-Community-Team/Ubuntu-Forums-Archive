---
title: "network-manager-vpnc won't connect"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by meatwad64 on 2008-03-02
I'm using hardy heron and when using network manager for connecting to a vpnc connection.

It won't work and errors out right away saying it can't connect to the vpn server. I have tried to ping the vpn server and it works just fine. It also works if i try to connect to it just using vpnc-connect from a terminal window. Anyone have any ideas what is wrong or is this just a bug ?

---

### Post by dedmonds on 2008-03-03
If you are able to connect with vpn-connect successfully, but not through the network manager, I suspect there may simply be a configuration problem. If I'm not mistaken, the network-manager-vpnc configuration VPN settings are separate from the settings (/etc/vpnc/default.conf file) used by vpnc-connect at the terminal. You can get to the Network Manager VPNC Connection settings by clicking on the Network Manager icon, going to VPN Connections and choosing Configure VPN.

---

