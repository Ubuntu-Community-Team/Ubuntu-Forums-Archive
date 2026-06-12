---
title: "VPN script"
date: 2015-06-11
forum: Networking &amp; Wireless
---

### Post by danne33 on 2015-06-11
Trying to make a script that connects my computer to a VPN server every time I log into the computer.
The following script is now located in /etc/NetworkManager/dispatcher.d/:
```
#!/bin/bash

REQUIRED_CONNECTION_NAME="Normal-connection"
VPN_CONNECTION_NAME="VPN-connection number 3"

activ_con=$(nmcli con status | grep "${REQUIRED_CONNECTION_NAME}")
activ_vpn=$(nmcli con status | grep "${VPN_CONNECTION_NAME}")
if [ "${activ_con}" -a ! "${activ_vpn}" ];
then
    nmcli con up id "${VPN_CONNECTION_NAME}"
fi
```

The problem with the script is that I can't disconnect from VPN-server.
Nor can I change the VPN-server to an other VPN-server.
Anyone know how to fix this problem?

---

