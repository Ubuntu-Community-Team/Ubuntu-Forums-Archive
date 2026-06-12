---
title: "Starting OpenVPN service"
date: 2017-11-03
forum: Networking &amp; Wireless
---

### Post by BigYellowDog on 2017-11-03
I'm running ubuntu server 16.04 LTS.  I'm not having any success starting the openvpn service.  I have a openvpn.conf file in /etc/openvpn.  I can start openvpn from the command line with no problems.
> sudo openvpn /etc/openvpn/openvpn.conf
When I try to start openvpn as a service it does not work
> 
$ sudo service openvpn status
&#9679; openvpn.service - OpenVPN service
   Loaded: loaded (/lib/systemd/system/openvpn.service; enabled; vendor preset: enabled)
   Active: active (exited) since Fri 2017-11-03 10:48:26 EDT; 8min ago
  Process: 16920 ExecStart=/bin/true (code=exited, status=0/SUCCESS)
 Main PID: 16920 (code=exited, status=0/SUCCESS)

Nov 03 10:48:25 ubuntu systemd[1]: Starting OpenVPN service...
Nov 03 10:48:26 ubuntu systemd[1]: Started OpenVPN service.


My understanding is openvpn will use any file ending in conf located in /etc/openvpn and use that as the server configuration to connect to.

---

