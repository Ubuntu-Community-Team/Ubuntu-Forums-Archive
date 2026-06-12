---
title: "[SOLVED] How to test whether connections are being tunnelled through VPN?"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by PartisanEntity on 2007-11-14
How can I check to see whether all connections; browser, chat and bittorrent are being tunnelled through the VPN connection?

---

### Post by Fire_Chief on 2007-11-14
What sort of VPN connection is it? IPSEC, PPTP? Are you using NetworkManager, a vendor VPN client, other?

---

### Post by PartisanEntity on 2007-11-14
PPTP through NetworkManager to Relakks.com

---

### Post by Fire_Chief on 2007-11-14
Well, a quick and easy way to tell is to run a traceroute while disconnected and then connect to the VPN and run the traceroute again. If the trace is the same (or very similar for the first 5-6 hops) then all traffic is not traveling over the VPN. This would lead to the conclusion that split tunneling is enabled (though I'm not sure this can be done over PPTP VPNs). Split tunneling allows only the traffic destined for the remote VPN subnet to go over the tunnel.

---

### Post by PartisanEntity on 2007-11-14
Thanks, the traceroute showed that the connection is going through the VPN, also, Firestarter can help identify the source and destination IP's I just noticed.

---

