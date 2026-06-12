---
title: "vpnbook (Openvpn) not connecting"
date: 2015-06-06
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2015-06-06
I have followed the vpnbook onsite instructions. I have set up a vpn network connection. Everytime I try to connect it fails with an error:

** Connection failed. Activation of network failed. **


I would very much appreciate some help because although this is an extract from my syslog, I do not understand what to change to correct the problems shown in the extract.

```
Jun  6 19:13:22 robins-EP35-DS3L NetworkManager[1033]: <info> VPN plugin state changed: init (1)
Jun  6 19:13:23 robins-EP35-DS3L NetworkManager[1033]: <info> VPN plugin state changed: starting (3)
Jun  6 19:13:23 robins-EP35-DS3L NetworkManager[1033]: <info> VPN connection 'vpnbook' (Connect) reply received.
Jun  6 19:13:23 robins-EP35-DS3L nm-openvpn[30050]: OpenVPN 2.3.2 i686-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [eurephia] [MH] [IPv6] built on Dec  1 2014
Jun  6 19:13:23 robins-EP35-DS3L nm-openvpn[30050]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Jun  6 19:13:23 robins-EP35-DS3L nm-openvpn[30050]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Jun  6 19:13:23 robins-EP35-DS3L nm-openvpn[30050]: Error: private key password verification failed
Jun  6 19:13:23 robins-EP35-DS3L nm-openvpn[30050]: Exiting due to fatal error
Jun  6 19:13:23 robins-EP35-DS3L NetworkManager[1033]: <warn> VPN plugin failed: 1
Jun  6 19:13:23 robins-EP35-DS3L NetworkManager[1033]: <info> VPN plugin state changed: stopped (6)
Jun  6 19:13:23 robins-EP35-DS3L NetworkManager[1033]: <info> VPN plugin state change reason: 0
Jun  6 19:13:23 robins-EP35-DS3L NetworkManager[1033]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
```

---

