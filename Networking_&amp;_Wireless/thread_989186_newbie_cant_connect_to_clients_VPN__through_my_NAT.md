---
title: "newbie cant connect to clients VPN  through my NAT."
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by wachaca on 2008-11-21
Hello,
I have several XP work stations, behind an Ubuntu server providing NAT for the office. 

When we had the DLINK router providing NAT, we were able to connect to a clients VPN based on PPTP/PPP using the windows VPN client without any problems.

Now we can no longer connect to the clients VPN.

My nat.sh file looks like this:
(I came up with this from diferent tutorials and howtos)

```
# Load the NAT module (this pulls in all the others).
modprobe iptable_nat

# In the NAT table (-t nat), Append a rule (-A) after routing
# (POSTROUTING) for all packets going out ppp0 (-o ppp0) which says to
# MASQUERADE the connection (-j MASQUERADE).
iptables -F
iptables -P FORWARD ACCEPT
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# Turn on IP forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward

```

Any help would be apreciated.

Thanks

---

