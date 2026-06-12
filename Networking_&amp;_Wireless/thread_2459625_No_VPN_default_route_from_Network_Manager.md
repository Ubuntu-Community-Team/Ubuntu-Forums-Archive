---
title: "No VPN default route from Network Manager"
date: 2021-03-22
forum: Networking &amp; Wireless
---

### Post by RayH on 2021-03-22
When I establish an OpenVPN session from Terminal my VPN session works fine and adds a default route to my routing table so that all traffic passes over the VPN tunnel (my preferred result).  However, if I establish the VPN connection via Network Manager the VPN session connects but does not add a default route, so I end up with no Internet.

Syslog shows the following when connecting via Network Manager
Mar 22 12:46:25 UbuntuDaily nm-openvpn[9105]: Initialization Sequence Completed
Mar 22 12:46:25 UbuntuDaily NetworkManager[563]: <info>  [1616431585.5673] vpn-connection[0x55b7399e2400,7f079478-0dd6-4f50-8a77-35fc824f16fd,"bbbbb",5:(tun1)]: Data:   Static Route: 0.0.0.0/0   Next Hop: 172.21.20.1
Mar 22 12:46:25 UbuntuDaily NetworkManager[563]: <info>  [1616431585.5673] vpn-connection[0x55b7399e2400,7f079478-0dd6-4f50-8a77-35fc824f16fd,"bbbbb",5:(tun1)]: Data:   Static Route: 172.21.20.0/23   Next Hop: 0.0.0.0

If I connect via OpenVPN it successfully adds the default route:
Mon Mar 22 12:49:13 2021 /sbin/ip route add 0.0.0.0/1 via 172.21.20.1

I built this system from the ground up, mini-iso 18.04.5 x64 build with a basic openbox/tint2 environment, so it's quite possible a setting is missing that would have been installed in a full DE.

---

### Post by RayH on 2021-03-22
During troubleshooting discovered that I can't ping next hop when establishing connection via network manager, so it must be an issue with the connection itself.

---

### Post by RayH on 2021-03-23
Still stumped on this.  Any idea why OpenVPN would work fine from command line but not from Network Manager?  It appears that as soon as the connection attempt starts that the computer loses all network connectivity before it can connect to the destination VPN server.

---

