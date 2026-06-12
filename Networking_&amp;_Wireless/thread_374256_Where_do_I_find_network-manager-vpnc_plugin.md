---
title: "Where do I find network-manager-vpnc plugin?"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by FIONEX on 2007-03-02
Hey,  I'm currently on xubuntu 6.10, and I have network-manager, network-manager-gnome, and network-manager-pptp installed.  I'm actually looking for network-manager-vpnc so that I can connect to a cisco vpn at my university.  I do have the "vpnc" package installed but connecting through the command line is a pain...  and the network kicks you off at random, so I don't see my self trying to reconnect every 5 minutes.  Where can I find the plugin network-manager-vpn?

---

### Post by FIONEX on 2007-03-02
Does anyone know if it even exists or is it part of the network-manager cvs source that I would have to compile on my own?

---

### Post by FIONEX on 2007-03-02
Ok, i just wasn't looking hard enough.  It wasn't in the respositories but I found it here:
[http://www.linux2go.dk/ubuntu/pool/main/n/network-manager-vpnc/](http://www.linux2go.dk/ubuntu/pool/main/n/network-manager-vpnc/)

When somebody searches for VPN, atleast they'll come up with this.

---

### Post by triwave on 2007-04-12
I found the .deb package but got lots of dependancy errors trying to install it. Is this suitable for Dapper 6.06 or do you need to be running a later version of ubuntu?

I'm trying to install on a lightweight (poor performance) laptop that is running 6.06 with xfce installed. 

I'd like to VPN into my companies server (Cisco) so that I could check e-mail through the webmail portal, even from this simple machine...

Wondering if it's possible to do that??

```
dpkg: dependency problems prevent configuration of network-manager-vpnc:
 network-manager-vpnc depends on libatk1.0-0 (>= 1.12.1); however:
  Version of libatk1.0-0 on system is 1.11.4-0ubuntu1.
 network-manager-vpnc depends on libbonobo2-0 (>= 2.15.0); however:
  Version of libbonobo2-0 on system is 2.14.0-0ubuntu2.
 network-manager-vpnc depends on libbonoboui2-0 (>= 2.15.0); however:
  Version of libbonoboui2-0 on system is 2.14.0-0ubuntu1.
 network-manager-vpnc depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.4.
 network-manager-vpnc depends on libcairo2 (>= 1.2.4); however:
  Version of libcairo2 on system is 1.0.4-0ubuntu1.
 network-manager-vpnc depends on libdbus-1-3; however:
  Package libdbus-1-3 is not installed.
 network-manager-vpnc depends on libdbus-glib-1-2 (>= 0.71); however:
  Version of libdbus-glib-1-2 on system is 0.60-6ubuntu8.1.
 network-manager-vpnc depends on libglib2.0-0 (>= 2.12.0); however:
  Version of libglib2.0-0 on system is 2.10.3-0ubuntu1.
 network-manager-vpnc depends on libgnome-keyring0 (>= 0.5.2); however:
  Version of libgnome-keyring0 on system is 0.4.9-1ubuntu1.
 network-manager-vpnc depends on libgnomevfs2-0 (>= 2.15.90); however:
  Version of libgnomevfs2-0 on system is 2.14.2-0ubuntu1.
 network-manager-vpnc depends on libgtk2.0-0 (>= 2.10.3); however:
  Version of libgtk2.0-0 on system is 2.8.20-0ubuntu1.1.
 network-manager-vpnc depends on liborbit2 (>= 1:2.14.1); however:
  Version of liborbit2 on system is 1:2.14.0-0ubuntu1.
 network-manager-vpnc depends on libpango1.0-0 (>= 1.14.5); however:
  Version of libpango1.0-0 on system is 1.12.3-0ubuntu3.
 network-manager-vpnc depends on libpopt0 (>= 1.10); however:
  Version of libpopt0 on system is 1.7-5.
 network-manager-vpnc depends on libxml2 (>= 2.6.26); however:
  Version of libxml2 on system is 2.6.24.dfsg-1ubuntu1.
```

---

