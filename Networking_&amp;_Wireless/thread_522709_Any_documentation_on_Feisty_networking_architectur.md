---
title: "Any documentation on Feisty networking architecture?"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by oddhack on 2007-08-10
I'm going nuts trying to figure out the relationship between the various pieces of networking software that come out-of-the-box with Ubuntu 7.04, particularly dbus / dhcdbd / network-manager. dhcdbd in particular is puzzling and essentially undocumented as best I can tell - /usr/share/doc/dhcdbd/README gives **no information whatsoever** about how dhcdbd is actually **used**, and by what (and the term "dhcdbd" appears nowhere else under /usr/share/doc, for that matter). In particular I'd like to know what is telling dhcdbd to start dhclient.

Is there anything out there documenting the architecture of Ubuntu networking - what services are started at boot, how those services are used, where all of their config files are located, which of those config files are amenable to manual manipulation and which are subject to arbitrary overwriting by helper apps, what the helper apps are?

I come from a Mandriva / Fedora background where this was all pretty straightforward - there were a static set of config files under /etc/sysconfig/{networking,network-scripts}, they were invoked in a predictable way by the network service and ifup/down, and there weren't any daemons running around stomping on the settings in those directories.

---

### Post by spd106 on 2007-08-13
I believe Network Manager uses DBus to communicate with dhcdbd, that's what it was created for.  
There is some specification documentation on the gnome website at [http://live.gnome.org/NetworkManagerConfigurationSpecification](http://live.gnome.org/NetworkManagerConfigurationSpecification), though that might not be exactly what you wanted.

The NM mailing list is probably the best source for information, try browsing the archives.
[http://mail.gnome.org/mailman/listinfo/networkmanager-list](http://mail.gnome.org/mailman/listinfo/networkmanager-list)

On a related note, this morning it was announced that dhcdbd has been removed from v0.7 trunk.
[http://mail.gnome.org/archives/networkmanager-list/2007-August/msg00094.html](http://mail.gnome.org/archives/networkmanager-list/2007-August/msg00094.html)

---

### Post by oddhack on 2007-08-13
> **spd106 said:**
> 
On a related note, this morning it was announced that dhcdbd has been removed from v0.7 trunk.
[http://mail.gnome.org/archives/networkmanager-list/2007-August/msg00094.html](http://mail.gnome.org/archives/networkmanager-list/2007-August/msg00094.html)

Better yet, I removed all of network-manager, dhcdbd, and laptop-net from my machine in favor of the much nicer WiCD package (wicd.sourceforge.net).

---

