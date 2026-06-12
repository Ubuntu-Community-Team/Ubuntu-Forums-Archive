---
title: "iptables - How do I restrict access to just local devices on the network?"
date: 2023-08-05
forum: Networking &amp; Wireless
---

### Post by fierce on 2023-08-05
I have a WireGuard VPN Server running on a Debian 12 host with no problems, listening on a specific UDP port, and all is working great with no issues.  I can connect from my phone WireGuard client while on 5G etc and all works as intended.

However I want to temporarily allow somebody access to this server, but restrict them to only accessing devices on my local network, 192.168.0.x - No access to the public internet once they are connected to the VPN so they can't visit general websites etc. just access devices on 192.168.0.x as needed

I am just a novice home user and tried this set of commands:

```

iptables -I OUTPUT -d 192.168.0.0/16 -j ACCEPT; iptables -P OUTPUT DROP
iptables -A INPUT -p udp -m udp --dport ##### -j ACCEPT
iptables -A INPUT -p udp -m udp --sport ##### -j ACCEPT

```
where ##### is the correct listening port to the outside world.  And on the host, generally seems to work as intended - I can communicate with all 192.168.0.0 devices and nothing outside of that scope - only problem is, I can also no longer connect via 5G to ######, my previously working VPN listen port.

Any assistance would be greatly appreciated, thank you!

Edit:

Another user told me to try FORWARD so I tried this but still no change, the daemon did not answer when tried from the outside world

```

iptables -I OUTPUT -d 192.168.0.0/16 -j ACCEPT; iptables -P OUTPUT DROP
iptables -A FORWARD -p udp -m udp --sport ##### -j ACCEPT
iptables -A FORWARD -p udp -m udp --dport ##### -j ACCEPT

```

---

### Post by #&amp;thj^% on 2023-08-05
All this can be very confusing and could leave you open for, well you know.
Have a look here: [https://www.linode.com/docs/guides/control-network-traffic-with-iptables/](https://www.linode.com/docs/guides/control-network-traffic-with-iptables/)

---

