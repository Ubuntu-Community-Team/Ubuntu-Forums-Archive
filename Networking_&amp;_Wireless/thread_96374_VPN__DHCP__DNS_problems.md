---
title: "VPN / DHCP / DNS problems"
date: 2005-11-28
forum: Networking &amp; Wireless
---

### Post by reuben on 2005-11-28
I think this is a bug in the default setup.

I am using pptpconf to connect to my VPN. (Had to dump firestarter and use guarddog instead.) 

Everything is fine except that the resolv.conf that pptpconf creates is periodically overwritten by the DHCP refresh of the DNS!! This is extremely annoying, as I have to start and stop the tunnel when this happens.

I don't want to turn off the DHCP refreshing of DNS, becasue I'm on a dynamic IP DSL connection (obviously I need DHCP to set it all up); HOWEVER, it should honor the fact that pptpconf has "control" of the resolv.conf (i.e. that I am using the tunnel)... 

How can I make this work?

---

### Post by dom on 2007-03-03
I have a similiar problem on Ubuntu Edgy (6.10).

I am using OpenVpn. I have a script that adds the Private network DNS (which is at the other end of the tunnel) and a "search" term to /etc/resolv.conf and brings up the tunnel connection. 
The script removes these entries when the VPN tunnel is taken down.

However, this info is lost periodically when my network connection is refreshed via DHCP.

I am also looking for a way to automatically keep the VPN settings while the VPN is up, regardless of what else changes.

Any suggestions appreciated.

---

