---
title: "Network Manager is not working"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by partymanbg on 2007-06-30
Hi all,

sorry for the silly qustion. A know there are a lot of postings about Network Manager, but no of them could help me.
 here what a have done: 

-i have installed network-manager-gnome on my ubuntu 6.10.
-the file /etc/network/interfaces file looks just fine(all lines besides the first 2 ones are commented). 
-i have added the entry "nm-applet --sm-disable" to the session startUp programms
-my Intell Pro/wireless 2200BG wirecard is installed

my problem:
i can not connect to internet, 
i can not even see the network manager icon in the notification area.
i dont know what to do!

10x for you help

---

### Post by walkerk on 2007-06-30
open terminal and:
```
nm-applet
```

what happens? nothing?

---

### Post by partymanbg on 2007-06-30
"nm-applet"  give this outputt:

** (nm-applet:7058): WARNING **: <WARNING>       nma_dbus_init (): nma_dbus_init() could not acquire its service.  dbus_bus_acquire_service() says: 'Connection ":1.21" is not allowed to own the service "org.freedesktop.NetworkManagerInfo" due to security policies in the configuration file'

---

### Post by partymanbg on 2007-06-30
sorry, i run "nm-applet" as root and this is what a get:

[B](nm-applet:7231): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/B]

---

