---
title: "How to control nm-applet from the command line?"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by leafw on 2008-01-20
Is it possible at all?
What I would like to do is the following:
- launch nm-applet in the background in a desktop environment that has no task bar
- communicate somehow with the nm-applet to make it connect to whatever network it has seen before.

The problem is that NetworkManager on itself does not connect, it's the applet that does so, And NetworkManager itself apparently cannot be controled from a command line either (its man page, and that of nm-applet, are very short and don't list all their possible arguments).

Using /etc/network/interfaces and sudo ifup ath0 is an option, but I can't never configure it correctly for wpa networks. The manual for iwconfig does not provide any examples of what s needed. But the nm-applet detects and connects to wpa just fine.

Any help appreciated.

---

### Post by spd106 on 2008-01-20
nm-applet talks to Network Manager over D-Bus. Going by the mailing list it's quite well known that the interface is not very well documented, but this is being worked on for the next release.

There isn't really an option for controlling Network Manager from the cli, though you might be able to implement your own using pynetworkmanager as a starting point.

I would recommend that you try reading the [Wireless Security sticky]("http://ubuntuforums.org/showthread.php?t=318539") for information about configuring WPA with wpa_supplicant and the interfaces file.

---

