---
title: "OpenVPN woring on all but ubuntu systems"
date: 2019-03-01
forum: Networking &amp; Wireless
---

### Post by petterg on 2019-03-01
I have a mikrotik rb3011 running openvpn server.
This works for mikrotik - mikrotik tunneling, gentoo - mikrotik, mac - mikrotik and windows - mikrotik.
However, ubuntu - mikrotik returns "error=unsupported certificate purpose"

On gentoo I've tested client versions 2.4.2, 2.4.4 and 2.4.6. All works.
On ubuntu I've tested version is 2.4.4.

Both the mac and ubuntu got their config file copied from the gentoo client.
I suspect there is some default config on ubuntu that makes the running config on this client differ from the others, despite identical config files. Does anyone have an idea of what needs to be done differently in ubuntu?

Client config
```

dev tun
proto tcp-client

remote server.example.local 1194

tls-client

#user nobody
#group nogroup

ca /configs/etc/openvpn/cert_export_ovpn-ca.crt

#comp-lzo # Do not use compression.

# More reliable detection when a system loses its connection.
ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key

mute-replay-warnings

verb 3

cipher BF-CBC
auth SHA1
pull

auth-user-pass /configs/etc/openvpn/auth.cfg

```

Client log
```

TCP_CLIENT link remote: [AF_INET]xx.xx.xx.xx:1194
 TLS: Initial packet from [AF_INET]xx.xx.xx.xx:1194, sid=f39e6cb9 1d26383b
 VERIFY ERROR: depth=0, error=unsupported certificate purpose: CN=ovpn-ca
 OpenSSL: error:1416F086:SSL routines:tls_process_server_certificate:certificate verify failed
 TLS_ERROR: BIO read tls_read_plaintext error
 TLS Error: TLS object -> incoming plaintext read error
 TLS Error: TLS handshake failed
 Fatal TLS error (check_tls_errors_co), restarting
 SIGUSR1[soft,tls-error] received, process restarting
 Restart pause, 300 second(s)

```

mikrotik server config
```

/interface ovpn-server server
set certificate=ovpn-ca cipher=blowfish128,aes128,aes192,aes256 default-profile=vpn-impact enabled=yes netmask=19

```

---

### Post by TheFu on 2019-03-01
Did you validate the file/directory paths for /configs/ stuff?  That's a non-standard place on Ubuntu - like - it doesn't usually exist.

Did you update the public server certificate on the ubuntu client?  I googled the error message and 
> Your client configuration holds a wrong ca certificate. If you copy the content from ca.crt to the <ca>-block of your client.conf file everything works. seems to be the answer.

Also, the client config file must have "client" in it. I use openvpn on an ubuntu server. It has worked with all the clients I've attempted.  I run both UDP and TCP versions, preferring the UDP when that works.  The tcp version is on 443, which goes through all the cheap hotel and business proxies fine.

```
$ more my-vpn.ovpn 
client
dev tun
proto udp
remote 50.xx.xx.xx 1194
resolv-retry infinite
nobind
persist-key
persist-tun
cipher aes-256-cbc
auth sha256
tls-client
remote-cert-tls server
auth-user-pass /etc/openvpn/login.cf
comp-lzo
verb 1
reneg-sec 0
crl-verify crl.rsa.4096.pem
ca ca.rsa.4096.crt
disable-occ
```
This works for me.  crl.rsa.4096.pem and ca.rsa.4096.crt are in the PWD.  I use IP addresses, not DNS, to avoid that little security problem with untrusted DNS in certain locations.

I would start by inserting "client" on a line as my first step. If that solves it, great!  And you wouldn't be the first to miss that. ;)

Next, I'd look at the SHA1 part.  SHA1 was deprecated, methinks:  [https://blog.qualys.com/ssllabs/2014/09/09/sha1-deprecation-what-you-need-to-know](https://blog.qualys.com/ssllabs/2014/09/09/sha1-deprecation-what-you-need-to-know)  There's a debian wiki entry about it somewhere.

---

