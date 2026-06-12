---
title: "OpenVPN Network Manager - HELP"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by lawson23 on 2008-03-08
OK so I installed the OpenVPN packages.
Network-manager-openvpn
openvpn

I have not installed any other packages.

Here is what I have.  I have my openvpn config file  (ovpn) for a user and all the cert files needed.  The config and certs work because I could connect from a windows box to the vpn server without issue.  Now I'm trying to do this through Linux Ubuntu Gutsy.

I went under network manager and selected vpn connections.  I then setup a vpn connection following my config file.

Now how do I get it to connect??????  Or if it is trying "how do I" know this?  I can click on the connection and nothing happens.  I would think a window would open showing the communication attempt.  Anyways it never gets connected.  I noticed there is a disconnect vpn button but no connect button.  Is there a log where I can see what is going on????

Please help as I'm a newb in need.

---------------------------------------------------------------
From a terminal I can do:
openvpn xxxx.ovpn

This does start openvpn and connect to the server.  What I get is:
```

Note: Cannot open TUN/TAP dev /dev/net/tun: Permission denied (errno=13)
Note: Attempting fallback to kernel 2.2 TUN/TAP interface
Cannot allocate TUN/TAP dev dynamically
Exiting
```



As a newb I have gone to the network manager's site and searched on this topic but can't find what I need.

---

### Post by lawson23 on 2008-03-08
Ok I fixed my terminal issue above by running:
sudo openvpn xxxx.ovpn

Now I can connect to my network.  I still would like to know what it is I'm doing incorrectly with Network Manager.

---

### Post by thefunnyman on 2008-03-11
try running the network manager as root.

Hope this helps

---

