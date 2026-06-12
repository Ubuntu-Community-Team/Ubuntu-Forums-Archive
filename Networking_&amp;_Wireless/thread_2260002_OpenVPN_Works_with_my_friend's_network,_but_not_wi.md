---
title: "OpenVPN: Works with my friend's network, but not with mine."
date: 2015-01-08
forum: Networking &amp; Wireless
---

### Post by SagaciousKJB on 2015-01-08
The other day I was at my friend's and tried out some VPN servers through VPNBook.  The OpenVPN ones worked just fine.  Well, later when I got home I tried again, and even though I could connect to the VPN I can't actually seem to connect to anything on a remote network.  For example if I try to ping 8.8.8.8, it doesn't even time out or anything it just sits there not producing any output at all...

Is it possible that there's something going on with my router or internet service that's preventing OpenVPN from working correctly for me at home?  I looked up some information for my router and it says that it supports L2PT/IPSec and PPTP explicity, but not openvpn.  I wouldn't think that such services were dependent upon router support.

I'm downloading Wireshark now to see if I can get a better idea of what's happening to the packets I'm sending but it's very confusing and I feel like it's not something wrong with my local configuration but rather my home network and router.

---

### Post by SagaciousKJB on 2015-01-08
Well not really sure what to look for with Wireshark. It just shows SYN packets being sent out, with nothing coming back.  In fact, I tried to ping and traceroue to the gateway that the openvpn server assigned me and it was as if there was something wrong with the routing.

So with that in mind...  Here's the routing table it configures.  Nothing jumps out at me as being wrong...

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.10.6.66      0.0.0.0         UG    0      0        0 tun0
10.10.0.1       10.10.6.66      255.255.255.255 UGH   0      0        0 tun0
10.10.6.66      *               255.255.255.255 UH    0      0        0 tun0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
free-vpn.torvpn 192.168.0.1     255.255.255.255 UGH   0      0        0 wlan0
192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0
```

Perhaps there is something I need to forward with iptables?  Currently all chains are set to "ACCEPT"...

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

...and again all this worked just fine on my firend's network.  I'm not sure what at all is different, except that I know my router uses NAT to connect to my ISPs network, and my friend's is just a straight-through cable modem.

---

