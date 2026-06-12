---
title: "Wireguard client not connecting to VPN server"
date: 2024-04-23
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2024-04-23
I have a client running wireguard.  I issue the `wg-quick up wg0` command, and it outputs the following:
`[#] ip link add wg0 type wireguard
[#] wg setconf wg0 /dev/fd/63
[#] ip -4 address add 192.168.4.5/32 dev wg0
[#] ip link set mtu 1420 up dev wg0
[#] wg set wg0 fwmark 51820
[#] ip -4 route add 0.0.0.0/0 dev wg0 table 51820
[#] ip -4 rule add not fwmark 51820 table 51820
[#] ip -4 rule add table main suppress_prefixlength 0
[#] sysctl -q net.ipv4.conf.all.src_valid_mark=1
[#] nft -f /dev/fd/63
`
I do a `sudo wg show`, and it shows my wg0 interface, and the peer, with the endpoint, and latest handshake of about 42 seconds ago.  
When I go to access a client on the other end of my network, the page does not load.
I also have this configured on my phone, and I am able to successfully connect to a host on the other end.
When I search for my IP on the internet, it shows my ip as the ip of that vpn server. 
I noticed when I run `ip route` before and after issuing the `up` command, that does not change.  Is this the culprit?

---

