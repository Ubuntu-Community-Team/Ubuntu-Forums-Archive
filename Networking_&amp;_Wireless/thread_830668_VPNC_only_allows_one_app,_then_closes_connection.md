---
title: "VPNC only allows one app, then closes connection"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by oniichan on 2008-06-16
This all started after installing the updates for 8.04 about a week ago. There is no problem making a connection to the Cisco VPN at work using either vpnc or vpnclient (cisco's vpn clinet for linux). Nor do I have a problem connecting to the remote computers via ssh, vncviewer, or rdesktop across the vpn. ONCE. It seems that when I close the client, it closes the vpnc connection. For example, once the vpnc connection is made, I connect to one of the network computers using 'ssh jim@runge'. When I exit that session, the vpn connection also closes. Same thing happens with vncviewer or rdesktop. Exiting the session also closes the vpn connection. So I have to log into the vpn all over again to use another client. This one even has the IT guys at work stumped. Any ideas?

It was due to a strange interaction between the ATT wireless router and Ubuntu. Resolv.conf was replaced when any app was closed. The router was configured in a mode they called 'DMZplus' which makes the client address the network IP address (not a DHCP).  By setting up a public proxied subnet (NAT/Routed)  'resolvconf' was fooled into keeping the resolv.conf.

---

