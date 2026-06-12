---
title: "Share only VPN connection"
date: 2014-10-17
forum: Networking &amp; Wireless
---

### Post by honeybadger2 on 2014-10-17
Hi, I am trying to setup a server to share a vpn connection and only the vpn connection. I have one lan that all computers are on and one internet connection. I want to be able to connect to the vpn in Ubuntu and share the connection on the same lan by setting the gateway in the other systems to the Ubuntu server.

I have got it to work by using the below however if the vpn connection disconnects the sharing then resorts back to the direct internet connection. I don't want it to do this, I simply want the connecting machines to have no internet access until the vpn comes back up.

Can this be done?

I have also found that if I only execute the first postrouting masquerade command, when the vpn connection comes back up the client pcs revert back to the vpn ip address. However if I use all of these commands when the vpn comes back up the original internet connection is still used?

Thanks

echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o tun0 -j MASQUERADE
iptables -A FORWARD -i tun0 -o eth0 -m state –-state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i eth0 -o tun0 -j ACCEPT

---

