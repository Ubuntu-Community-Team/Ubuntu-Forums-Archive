---
title: "feisty slow boot -- &quot;permanent&quot; edits on etc/network/interfaces?"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by raul on 2007-06-01
i did a fresh feisty install and it was booting up *very* slow. i started it in recovery mode to see where it was stalling, and it was in "configuring network interfaces". reading through a few threads i saw that some people had fixed this by commenting out all but a couple of lines of /etc/network/interfaces. i did that and feisty booted up in a breeze. the problem is that every time i manually start my wireless network (already in an x session), /etc/network/interfaces gets edited back. so when i restart it stalls again on configuring network interfaces while booting up. i already disabled session saving, and disabled the network manager in session startup, but it didn't help. does anyone know how can i edit /etc/network/interfaces so that it doesn't get re-edited when i start my wireless network manually? 

here's the original /etc/network/interfaces (eth1 is my wireless network):

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth1 inet dhcp
wireless-essid sweetiepie

auto eth1
```

here's how i edited it for fast booting:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


#iface eth1 inet dhcp
#wireless-essid sweetiepie

#auto eth1
```

here's how it gets edited back when i start eth1 manually:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


#iface eth1 inet dhcp
#wireless-essid sweetiepie


#auto eth1

iface eth1 inet dhcp
wireless-essid sweetiepie


auto eth1
```

any suggestions would be great. thanks in advance.

---

### Post by --Ja-- on 2007-06-01
I can't say that i know correct solution to your problem, but perhaps chmoding it to read only would help?

:popcorn:

---

### Post by raul on 2007-06-01
did sudo chmod -w, but it's still being written on

---

### Post by chili555 on 2007-06-01
Is this an Intel Pro Wireless 3945 by any chance? [https://bugs.launchpad.net/ubuntu/+bug/108152](https://bugs.launchpad.net/ubuntu/+bug/108152)

---

### Post by --Ja-- on 2007-06-01
> **raul said:**
> did sudo chmod -w, but it's still being written on

try chmod 444 /etc/network/interfaces just to be sure... I'm not sure how does -w behave in combination with sudo...

:popcorn:

---

### Post by raul on 2007-06-01
chili555: ipw3945 indeed; your work around did it for me, too. thanks a bunch! thank you too, --Ja--.

---

