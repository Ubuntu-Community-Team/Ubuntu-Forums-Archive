---
title: "OpenVPN trouble after upgrade to 8.10"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by vcba79 on 2008-11-03
Hi, all

I have a VPN server which I can connect from old ubuntu 8.04 installation. After upgrade to 8.10, I see following error in syslog:

--- log start --
Nov  4 12:33:06 lenovo NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.openvpn'...
Nov  4 12:33:06 lenovo NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 7000
Nov  4 12:33:06 lenovo kernel: [  615.522572] tun: Universal TUN/TAP device driver, 1.6
Nov  4 12:33:06 lenovo kernel: [  615.522583] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Nov  4 12:33:06 lenovo NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections
Nov  4 12:33:06 lenovo NetworkManager: <info>  VPN plugin state changed: 1
Nov  4 12:33:06 lenovo NetworkManager: <info>  VPN plugin state changed: 3
Nov  4 12:33:06 lenovo NetworkManager: <info>  VPN connection 'AmJet' (Connect) reply received.
Nov  4 12:33:06 lenovo nm-openvpn[7009]: OpenVPN 2.1_rc11 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Oct 15 2008
Nov  4 12:33:06 lenovo nm-openvpn[7009]: WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Nov  4 12:33:06 lenovo nm-openvpn[7009]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Nov  4 12:33:06 lenovo nm-openvpn[7009]: Cannot load private key file /u00/user/vincent/openvpn/vincent.key: error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch
Nov  4 12:33:06 lenovo nm-openvpn[7009]: Error: private key password verification failed
Nov  4 12:33:06 lenovo nm-openvpn[7009]: Exiting
Nov  4 12:33:06 lenovo NetworkManager: <info>  VPN plugin failed: 1
Nov  4 12:33:06 lenovo NetworkManager: <info>  VPN plugin state changed: 6
Nov  4 12:33:06 lenovo NetworkManager: <info>  VPN plugin state change reason: 0 
--- log end --

All certificates and private key files are copied from a working openvpn windows client configuration. Also, private key password remove using openssl. It works fine under 8.04, but I don't know why 8.10 get trouble.

I have the following setting in configuration tabs:

<VPN>
Authentication
type: certificate (TLS)
user certificate: vincent.pem
ca certificate: ca.pem
private key: vincent.key (password removed)
private key password: <empty>


Any idea?

Vincent

---

### Post by rowerdave on 2008-12-22
Hi,

Check your server.conf file that the server keys are being pointed to correctly.

/D

---

