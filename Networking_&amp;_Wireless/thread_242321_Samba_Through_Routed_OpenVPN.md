---
title: "Samba Through Routed OpenVPN"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by fawwaz on 2006-08-23
Few days ago I posted a thread about OpenVPN. It was my first encounter with OpenVPN configuration on UbuntuBOX I dedicated to be VPN server, firewall, router etc. (although it's not recommended to have VPN on firewall machine).

Here is my tunnel:
MyOffice > router/firewall > Internet > UbuntuBOX-(home)-VPN-Router-Firewall > eth1-WinBOX & eth2-UbuntuBOX-(desktopPC)

Routed OpenVPN (as it is said) was much easier to setup than Bridged OpenVPN. Now I have it all working - except filesharing. Broadcasts do get through virtual network but transfers are extremely slow (1-40KB/min) - I have 512Kbps on both sides.

Now - my question is: has anybody an idea how to setup WINS without bridged interfaces? Is it possible to have Samba fully active only on virtual network as domain master?

I can reach clients on both sides with explicit \\clientName or \\clientVirtual-IP.. I understand why they are not showing in both NetworkNeighbourhoods and I would like to resolve this through routed (not bridged) interfaces.

Regards.

---

