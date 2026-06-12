---
title: "OpenVPN on 8.10"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by Pruocchio on 2008-10-31
I just completed the upgrade to 8.10, and all went well, except that my openvpn configurations no longer work.  I use KVpnc as my front end, and what worked perfectly on 8.04, now refuses to connect.  I get the following:

info: Trying to connect to server "24.199.195.254" with ... 
debug: "openvpn" started.
info: [openvpn]: Low level connection to 24.199.195.254 established.
error: OpenvpnManagementHandler: Got no greeting within 3 seconds from management interface, retrying.
success: Successful connect try canceled.

Any thoughts?
Thanks,
Paul

---

### Post by Matthileo on 2008-10-31
On a semi-related issue I can't access VPN configuration from the network manager.  The add button is disabled.

---

### Post by ddarsow on 2008-10-31
I am having a similar issue as well. I can access my wireless at home fine, but the VPN connection at the law school no longer works. I am using vpnclient-linux 4.8.00 (Cisco) and have the exact same settings I had in Hardy before the upgrade.

---

### Post by pather on 2008-11-01
I'm having exactly the same situation as Pruocchio.
It seems we need to wait for some update :)) 

One way or the other, total lack of GUI for openvpn for gnome is irritating. I use OS X on my other computer and theres realy nice frontend called Tunnelblick. I wish something like this would be for Gnome as well :))

All other stuff works realy great and 8.10 seems like real upgrade from Hardy, which was not lucky one :))

---

### Post by pather on 2008-11-01
SOLUTION
I've just installed package network-manager-openvpn, set up maj crt and key files and IT WORKS! :)

so, no need for KDE app for Gnome :)


Have a nice day :)

---

### Post by cheetooh on 2008-11-11
> **pather said:**
> SOLUTION
I've just installed package network-manager-openvpn, set up maj crt and key files and IT WORKS! :)

so, no need for KDE app for Gnome :)


Have a nice day :)

Thank u pather... nice tips n really help me!

---

