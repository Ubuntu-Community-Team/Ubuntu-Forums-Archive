---
title: "Problems switching from vpnc to network-manager-vpnc"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by kryptonik on 2008-04-24
Hey all-

I want to switch from using the command line vpnc client to the network manager plugin.  I have a vpnc conf file that works fine, and that I've been using for a while.  I set up the network manager VPN connection using information from the conf file, but it doesn't seem to be able to create a connection to the network.  Worse, no errors are printed out anywhere!

Can someone point me to where the error log is for the network manager so that I can try to figure out what's going on?

Thanks!
-Rob

---

### Post by mkokotovich on 2008-05-15
Hi, first kill network manager:
As root,
```

# killall NetworkManager NetworkManagerDispatcher 

```
Then restart it, telling it not to daemonize
```

# NetworkManager --no-daemon

```

This will print messages to the terminal.  I am having what appears to be the same problem as you, mine comes down to this error:

** (process:16186): WARNING **: <WARNING>	 nm_vpnc_dbus_init (): Could not acquire the dbus service.  dbus_bus_request_name() says: 'Connection ":1.8037" is not allowed to own the service "org.freedesktop.NetworkManager.vpnc" due to security policies in the configuration file'

---

### Post by kryptonik on 2008-05-16
Actually, one of the recent upgrades seems to have fixed the problem.  I can now VPN into my network!

---

