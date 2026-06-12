---
title: "opnvpn network manager"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by b4nsh33 on 2008-09-10
hi, im trying to configure network manager to use vpn connection using shared key as authentication method, i have the vpn server running in a freebsd (pfsense) box and several windows xp using it, this is the client config settings:

client
dev tun
proto udp
remote 200.13.X.Y 1196
resolv-retry infinite
nobind
persist-key
persist-tun
secret keytmp.key
comp-lzo
verb 3


the problem is that network manager insists in asking for local ip and remote ip in the wizard if i select shared key as connection type, what should i put there?
 those params are not needed if i configure openvpn using the above settings.

---

### Post by b4nsh33 on 2008-09-10
Excuse my ignorance,  i re-read  the docs ans discovered that shared secret only supports one server, one client, so it needs a local and remote ip address scheme, according to openvpn docs:

Static Key disadvantages

    * Limited scalability -- one client, one server
    
    


So, no road warriors, 
Kind regards

---

