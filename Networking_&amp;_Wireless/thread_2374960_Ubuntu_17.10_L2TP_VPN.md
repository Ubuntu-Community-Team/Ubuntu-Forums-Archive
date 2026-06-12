---
title: "Ubuntu 17.10 L2TP VPN"
date: 2017-10-20
forum: Networking &amp; Wireless
---

### Post by Lee_Henderson on 2017-10-20
Very impressed, fast, all works, connections to SMB servers, WebDAVS all works.  Dual monitor support is now much better.  The last thing stopping me from moving to Mac OS X to Ubuntu is L2TP VPN support.  Its a must have for me.  So is there a way to get this working, that actually works.  Ive been through loads of things, none of them connect.  Can somebody help please?

---

### Post by Lee_Henderson on 2017-10-20
On the Mac, you just select VPN, then L2PT IPSec, enter the address, user/password and shared key, thats it, it works

---

### Post by #&amp;thj^% on 2017-10-20
> **Lee_Henderson said:**
> On the Mac, you just select VPN, then L2PT IPSec, enter the address, user/password and shared key, thats it, it works

Ubuntu has stopped shipping L2TP over IPSec support for Ubuntu since Precise. A workaround for this exists using network-manager-l2tp.
See this work around: [https://drive.google.com/file/d/0B9vaBliUPd9tQXNpMWNQeUhHWTA/view](https://drive.google.com/file/d/0B9vaBliUPd9tQXNpMWNQeUhHWTA/view)
Good Luck

---

### Post by Lee_Henderson on 2017-10-21
Thanks, I think I did this before under Ubuntu 16.0.4, and 17.0.4 but I will try again

---

### Post by joye2 on 2017-10-21
> **Lee_Henderson said:**
> Very impressed, fast, all works, connections to SMB servers, WebDAVS all works.  Dual monitor support is now much better.  The last thing stopping me from moving to Mac OS X to Ubuntu is [L2TP VPN]("https://www.mostsecurevpn.com/best-vpn-for-torrenting-p2p-filesharing/") support.  Its a must have for me.  So is there a way to get this working, that actually works.  Ive been through loads of things, none of them connect.  Can somebody help please?
What kinda VPN provider you are using, is that third party?

---

### Post by dkosovic on 2017-10-21
Is there something wrong with the version of network-manager-l2tp that ships with Ubuntu 17.10?

[https://packages.ubuntu.com/artful/network-manager-l2tp-gnome](https://packages.ubuntu.com/artful/network-manager-l2tp-gnome)

Ubuntu 17.10 ships with both libreswan and strongswan for IPsec support and either can be used with network-manager-l2tp

---

### Post by Lee_Henderson on 2017-10-22
Im connecting to L2TP IPSec VPNs that are controlled via Mac OS Server 10.11/10.12 and 10.13.  Windows connects, iOS/Mac OS, but its always a problem from Ubuntu.  Is this not industry standard tech?

---

### Post by dkosovic on 2017-10-23
The two most common reasons why network-manager-l2tp doesn't allow you to connect to a VPN server:

**1. Issue with not stopping system xl2tpd service**, see the README.md file :

[https://github.com/nm-l2tp/network-manager-l2tp#issue-with-not-stopping-system-xl2tpd-service](https://github.com/nm-l2tp/network-manager-l2tp#issue-with-not-stopping-system-xl2tpd-service)

Although the use of an ephemeral port is considered acceptable in RFC3193, the L2TP/IPsec standard co-authored by Microsoft and Cisco, there are some L2TP/IPsec servers and/or firewalls that will have issues if an ephemeral port is used. An ephemeral port is used when the system xl2tpd (or other L2TP service) hasn't been stopped.

Other Linux distributions like Fedora, don't have the system xl2tpd service running by default.

[B]
2. Your VPN server is using a legacy IPsec cipher that strongswan considers broken[/B] as it is old and weak.

See the "User specified IPsec IKEv1 cipher suites" section in the README.md file :

[https://github.com/nm-l2tp/network-manager-l2tp#user-specified-ipsec-ikev1-cipher-suites](https://github.com/nm-l2tp/network-manager-l2tp#user-specified-ipsec-ikev1-cipher-suites)

it has an example of how to specify old legacy ciphers for the Phase 1 and 2 algorithms in the IPsec config dialog box which are then used to for the proposals to negotiate with the VPN server.

Alternatively you can replace strongswan with libreswan that ships with Ubunto 17.10 and doesn't haven't the same legacy IPsec algorithms issues by installing with :

[FONT=courier new]sudo apt install libreswan[/FONT]

Note: this workaround for broken ciphers by using libreswan won't work for libreswan > 3.20 that will ship with Ubunto 18.04, and will require the same Phase 1 & 2 Algorithm setup as strongswan.

---

### Post by dkosovic on 2017-10-24
Forgot to mention, unless you still have WinXP or earlier VPN clients, there is no reason to only offer the broken 3DES algorithm with L2TP/IPsec servers.

---

