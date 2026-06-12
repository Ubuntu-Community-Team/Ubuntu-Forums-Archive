---
title: "OpenVPN issues"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by tehsilverdollar on 2008-07-17
I'm having issues connecting to an openvpn server at my workplace.  The only error messages i could find are in the syslog

> Jul 17 07:51:10 buntu openvpn[6526]: OpenVPN 2.1_rc7 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] built on Jun 11 2008
Jul 17 07:51:10 buntu openvpn[6526]: Cannot load private key file /home/dan/vpn/Dan_Therrien.key: error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch
Jul 17 07:51:10 buntu openvpn[6526]: Error: private key password verification failed
Jul 17 07:51:10 buntu openvpn[6526]: Exiting

I have tried starting VPN both with the network manager and from the command line.  From the network manager i get a popup message saying

> VPN Connect Failure

Could not start the VPN connection 'Work' due to a connection error.

The VPN login failed because the VPN program could not connect to the VPN server.

All of my certs and keys are read/writeable to the world until i figure this out.  I've tried the hack fix for openssl-vulnkey and have been unable to find any help elsewhere on this.  Here's my config file as well...i've replaced the domain with domain.com for security reasons

> 
client
tls-client
port 1195
ns-cert-type server
remote domain.com
dev tun
ca /home/dan/vpn/cacert.pem
cert /home/dan/vpn/Dan_Therrien.pem
key /home/dan/vpn/Dan_Therrien.key
tls-auth /home/dan/vpn/ta.key 1
comp-lzo
keepalive 10 60
ping-timer-rem
persist-key
persist-tun
user nobody
group nobody
daemon
verb 3
mute 10
# tun-mtu 1500
# fragment 1300
# mssfix 1300


If anybody is good at this kind of stuff, please let me know if you can help.

---

