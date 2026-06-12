---
title: "Network-Manager not working after joining AD"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by kboren on 2007-06-24
To make a long story short, I had the wireless card working fine until I joined my PC to windows active directory and now the network-manager will no longer work.  I know it is a permissions issue because of the message I get when I run the following command: nm-applet --sm-disable

I get this repeating error:

** (nm-applet:8269): WARNING **: <WARNING>       nma_dbus_init (): nma_dbus_init() could not acquire its service.  dbus_bus_acquire_service() says: 'Connection ":1.36" is not allowed to own the service "org.freedesktop.NetworkManagerInfo" due to security policies in the configuration file'

Any help would be appreciated.  There is no wired connection for the PC so I have to use the wireless and it needs to be part of active directory so I need to get this fixed, thanks in advance.

---

### Post by jonj on 2007-07-11
I have the same problem.  I think nm-applet stopped working after I installed the CISCO vpn client (from cisco, not vpnc).

Any Ideas please?

My user is already a member of netdev which is the fix suggested on some debian forums.

thanks,
J

---

### Post by jonj on 2007-07-11
I can confirm that the CISCO vpn client stopped nm-applet from starting in my case because nm-applet works now that I've uninstalled the cisco client ( vpnclient-linux-4.8.00.0490-k9.tar.gz )

Really they should both work at the same time! I'll be trying vpnc as an alternative to the cisco client.

J

---

