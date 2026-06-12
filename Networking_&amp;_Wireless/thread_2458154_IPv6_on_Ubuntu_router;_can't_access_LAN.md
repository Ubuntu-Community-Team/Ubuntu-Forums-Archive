---
title: "IPv6 on Ubuntu router; can't access LAN"
date: 2021-02-17
forum: Networking &amp; Wireless
---

### Post by rbf on 2021-02-17
Hey all,

I have a router running Ubuntu 20.04 that is statically configured via netplan for the LAN interface and dhcp/dhcp6 for the WAN interface. Everything works as expected EXCEPT the router itself cannot use/ping via IPv6 on the LAN side. 

To be clear: IPv6 and IPv4 work to WAN side for the router, machines on the LAN side have fully working IPv6 and IPv4, and the router has working IPv4 on the LAN, it is only the router that is unable to use IPv6 on the LAN side. My ISP has provided a /64 for IPv6 usage and I have dhcp (IPv4), dhcp6 (IPv6), and radvd all set up and working.

I've tried assigning a gateway6 address to eno1 (the LAN side) but networkctl tells me "eno1: Could not set route: Gateway can not be a local address. Invalid argument"

If I leave gateway6 out of the config there are no errors but the router can't use IPv6 on the LAN yet machines on the LAN can. It seems like the router can't figure out it is it's own route for the /64.

My netplan config looks like this:
```

network:
        version: 2
        renderer: networkd
        ethernets:
                enp2s0:
                        macaddress: XX:XX:XX:XX:XX:XX
                        dhcp4: true
                        dhcp6: true
                        dhcp4-overrides:
                                use-dns: false
                        dhcp6-overrides:
                                use-dns: false
                        nameservers:
                                search: [my local domain]
                                addresses: [127.0.0.1]
                eno1:
                        macaddress: XX:XX:XX:XX:XX:1
                        dhcp4: false
                        dhcp6: false
                        addresses:
                                  - 192.168.13.1/24
                                  - XXXX:XXX:XXX:XXX::1/64
                        nameservers:
                                search: [my local domian]
                                addresses: [127.0.0.1]

```



Any help would be greatly appreciated! Thank you!

---

**SOLVED**: I solved the issue by adding "accept-ra: yes" to the network configuration section for eno1. Now ping from the router works as expected.

---

### Post by The Cog on 2021-02-17
In future, please use code tags when posting netplan config - indentation is crucial. If you "go advanced" when composing, there is a '#' button that enters code tags. 

You say IPv6 ping isn't working on the LAN. Are you trying to ping other LAN PCs from the router, or ping the router from PCs on the LAN, or ping things on the internet from the LAN?

Assuming you are trying to ping other LAN hosts from the router, are you sure they are in the same network range (first 64 bits the same)? 
Check that the router knows the right way to talk to them, with "ip route get <address>" and make sure it's not wanting to send towards the internet.
After trying to ping, use "ip -6 neighbor" to see if the address has been resolved to a MAC address properly.

Let's see where the above checks lead.

---

### Post by The Cog on 2021-02-18
> SOLVED: I solved the issue by adding "accept-ra: yes" to the network configuration section for eno1. Now ping from the router works as expected. 
Nice one! Thanks for the update. I must remember that.

---

