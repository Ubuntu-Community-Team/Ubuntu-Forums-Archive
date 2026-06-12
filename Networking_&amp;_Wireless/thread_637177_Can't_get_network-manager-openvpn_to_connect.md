---
title: "Can't get network-manager-openvpn to connect"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by darkshadow on 2007-12-10
I just install the vpn version of dd-wrt on my router and setup the vpn server. I have even got it to work when manually running the openvpn command on my laptop with the following config file

   remote XXXX.dyndns.org
   port 443
   dev tap
   secret static.key
   proto tcp-client
   comp-lzo
   route-gateway 192.168.1.1
   redirect-gateway


But when I try putting all that in network-manager it well not work. I assume it is because it asks for "local ip" and "remote ip" under the "shared key" box, and I don't know what to put  their as everything I tried did not work.

---

### Post by SnakeEater251 on 2008-05-11
I also cannot get the openvpn client to route any traffic through the vpn. I've tried pinging an address local to the remote network, but I get 100% packet loss.

I have dd-wrt installed on my router, with openvpn server set up on it. I have already tested the following configuration with OpenVPN GUI on windows, and full traffic routing works fine.

This is my client configuration:
```
remote remoteserver.org
port 1194
dev tap
secret static.key
proto udp
comp-lzo
route-gateway 192.168.1.1
redirect-gateway
```

Thank you in advance for any help.

---

