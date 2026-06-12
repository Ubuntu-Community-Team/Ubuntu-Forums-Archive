---
title: "Network namespace with wireless connection"
date: 2020-04-06
forum: Networking &amp; Wireless
---

### Post by mertho on 2020-04-06
hi,

i have an ethernet and wireless connection.
now i want to create a network namespace and everything within that namespace should connect to the internet through the wireless connection.

here is what i have so far:
```

ip netns add customns

ip link add vcustomns0 type veth peer name vcustomns0_peer
ip link set vcustomns0_peer netns customns


ip addr add 192.168.1.1/24 dev vcustomns0
ip link set vcustomns0 up

ip netns exec customns ip addr add 192.168.1.2/24 dev vcustomns0_peer
ip netns exec customns ip link set dev lo up
ip netns exec customns ip link set dev vcustomns0_peer up
ip netns exec customns ip route add default via 192.168.1.1


iptables -A FORWARD -o wlp0s20f3 -i vcustomns0 -j ACCEPT
iptables -A FORWARD -i wlp0s20f3 -o vcustomns0 -j ACCEPT
iptables -t nat -A POSTROUTING -s 192.168.1.1/24 -o wlp0s20f3 -j MASQUERADE

```

when i want to ping e.g. 8.8.8.8 from the network namespace nothing happens.
if i replace the iptables section with the following i have an internet connection.
```

iptables -A FORWARD -o eno1 -i vcustomns0 -j ACCEPT
iptables -A FORWARD -i eno1 -o vcustomns0 -j ACCEPT
iptables -t nat -A POSTROUTING -s 192.168.1.1/24 -o eno1 -j MASQUERADE

```

why does this work via the ethernet interface but not via the wireless interface?
what i'm missing, im stuck :)

br

---

