---
title: "Network Manager icon randomly disappearing"
date: 2014-07-04
forum: Networking &amp; Wireless
---

### Post by typically2 on 2014-07-04
Using 14.04, after the most recent set of updates, the icon is disappearing at random from the top panel.

Seems to require a reboot to get it back.

This doesn't work:

```

typically@typically-laptop:~$ sudo service network-manager stop
network-manager stop/waiting
typically@typically-laptop:~$ sudo rm /var/lib/NetworkManager/NetworkManager.state
typically@typically-laptop:~$ sudo service network-manager start

```

Neither does this:

```

sudo nm-applet &
[1] 6734
typically@typically-laptop:~$ nm-applet-Message: using fallback from indicator to GtkStatusIcon

```

One of a multitude of little things that have broken with updates...

Any help appreciated, thanks!

---

