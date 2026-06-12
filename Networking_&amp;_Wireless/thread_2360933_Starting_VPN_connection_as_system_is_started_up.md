---
title: "Starting VPN connection as system is started up"
date: 2017-05-10
forum: Networking &amp; Wireless
---

### Post by David_Partridge on 2017-05-10
I have a VPN connection that I want to bring up as the system is booted.

Currently it is defined in "Network Manager" and I need to select the entry for it from "VPN Connections" and then enter the password to access the default keyring (I assume my personal one).

How can I configure this to start automagically as the system is coming up without needing password prompts or similar?

Thanks in advance
Dave

---

### Post by TheFu on 2017-05-10
There are probably a few ways to accomplish this.

I would:
* manually configure networking using the standard methods** /etc/networking/interfaces**
* add a *post-up* command that brings up the VPN
* run the VPN using a script. What that needs depends on the specific VPN type used.  I use openvpn, so 
```
#!/bin/bash
cd /etc/openvpn
/usr/sbin/openvpn UK_London.ovpn &
```
I'm using a login.cf file for the VPN credentials, it is configured inside the different .ovpn files.

No need to shutdown the VPN, but if you need to, there is a *pre-down* command for the interfaces file too.

This works best for desktops and servers.  On a computer that moves around all the time, you probably want it manually started. Too many issues can happen due to being on strange networks where a human needs to be involved.

**man interfaces** has more details.

Oh - and if you go with the interfaces file method (which is standard on servers), then you can't use network-manager for that interface anymore. If the system doesn't move, this isn't an issue.

---

### Post by David_Partridge on 2017-05-10
I reconfigured to NOT use Network manager, and created a .ovpn configuration file for privateinternetaccess.com's UK Southampton node:

```
client
dev tun
proto tcp
remote uk-southampton.privateinternetaccess.com 501
resolv-retry infinite
nobind
persist-key
persist-tun
cipher aes-128-cbc
auth sha256
tls-client
remote-cert-tls server
auth-user-pass .secret
comp-lzo
verb 1
reneg-sec 0
crl-verify pia-crl.rsa.4096.pem
ca pia-ca.rsa.4096.crt
disable-occ
```

which I tested using openvpn pia.ovpn.  Once I had it working right, I copied it to /etc/openvpn as pia.conf and added a .secret file for my PIA account to that directory with permissions 600 and owned by root:root

```

username
password
```

With the default openvpn configuration (/etc/defaults/openvpn), openvpn will autostart the vpns defined in ALL .conf files in /etc/openvpn.

In this case the only one that is started is pia as that's the only one there.

This works a treat and is really simple

Cheers
Dave

---

