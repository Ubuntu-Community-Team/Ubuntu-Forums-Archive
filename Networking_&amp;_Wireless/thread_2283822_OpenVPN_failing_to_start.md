---
title: "OpenVPN failing to start"
date: 2015-06-24
forum: Networking &amp; Wireless
---

### Post by readyrevolver on 2015-06-24
Hi - I've been using NetworkManager with OpenVPN to connect to my work VPN for months now. Yesterday it was working, then today when I went to connect I get this message:

"The VPN connection workvpn failed because the VPN service failed to start"

And this is all there is in syslog:

[FONT=courier new]Jun 25 11:39:13 jalapeno NetworkManager[5380]: <info> VPN connection 'workvpn' (ConnectInteractive) reply received.
Jun 25 11:39:13 jalapeno NetworkManager[5380]: <warn> VPN connection 'workvpn' failed to connect interactively: 'Method "ConnectInteractive" with signature "a{sa{sv}}a{sv}" on interface "org.freedesktop.NetworkManager.VPN.Plugin" doesn't exist#012'.[/FONT]

The only difference between yesterday and today is that yesterday I installed network-manager-vpnc in order to connect to a cisco vpn I had need to connect to. I've removed that package and restarted NetworkManager but still have the problem.

Any ideas?

---

