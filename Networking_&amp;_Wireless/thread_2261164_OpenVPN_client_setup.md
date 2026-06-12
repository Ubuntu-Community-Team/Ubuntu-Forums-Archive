---
title: "OpenVPN client setup"
date: 2015-01-16
forum: Networking &amp; Wireless
---

### Post by Mustafa_Khan on 2015-01-16
I' am trying to set up my raspberry pi (Raspbian) to connect to and use a vpn server according to a configuration file provided by the VPN service.

This config works really well on my Ubuntu PC but not on Raspbian.  I can connect to the server but am unable to ping any websites.  I'm not sure how to start troubleshooting this problem so if there are any networking experts here I would appreciate your input.

I know this isn't a Ubuntu related question but I've found this place to be very helpful in the past with questions relating to linux in general so I am posting here so please bear with me.  Here is the openvpn config file:

```
client

ping 5
ping-exit 30
dev tap
fast-io
proto udp


remote 93.115.92.240 443


resolv-retry infinite
nobind
persist-key
persist-tun


mute-replay-warnings


ca ca.crt
cert cactuspremium.crt
key cactuspremium.key


reneg-sec 0


ns-cert-type server


auth-user-pass login.conf


verb 3
```

---

