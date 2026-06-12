---
title: "intel 2200BG wireless connection issue"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by funesean on 2007-03-07
New to Linux and Ubuntu.  Installed 6.10 Edgy and on first boot wireless internet worked fine.  Every boot since it has not worked.  Trying to connect to unsecured campus network.  Works fine on dual booted windows.  Can see the access points in Wireless Connection Manager, but clicking connect does nothing.

The Network Tools panel shows eth1 having a IPv6 protocol, but not an IPv4 protocol.  It is receiving and sending packets, but again cannot connect to the access points and therefore no internet.

I haven't messed with the drivers in anyway as i know this card is supposed to work pretty much out of the box with Edgy, and for the first boot it did.   Be glad to provide more information if needed.  Thanks in advance - Sean

---

### Post by Floppyjoe on 2007-03-07
> **funesean said:**
> New to Linux and Ubuntu.  Installed 6.10 Edgy and on first boot wireless internet worked fine.  Every boot since it has not worked.  Trying to connect to unsecured campus network.  Works fine on dual booted windows.  Can see the access points in Wireless Connection Manager, but clicking connect does nothing.


What program are you using to try to connect with?What is the Wireless Connection Manager? Have you installed Network-Manager? If you have you need to disable all network interfaces in System/Administration/Networking for Network-Manager to work properly.

---

### Post by funesean on 2007-03-07
> **Floppyjoe said:**
> What program are you using to try to connect with?What is the Wireless Connection Manager? Have you installed Network-Manager? If you have you need to disable all network interfaces in System/Administration/Networking for Network-Manager to work properly.

Trying to connect with the Wireless Connection Manager that can be found [here]("http://gtkwifi.sourceforge.net/").  Just a panel to show available networks.

I did not install Network-Manager.

[B]SOLVED :  Added 
```
auto eth1
iface eth1 inet dhcp
```
to /etc/network/interfaces  where there was no eth1 reference in the file at all.[/B]

---

