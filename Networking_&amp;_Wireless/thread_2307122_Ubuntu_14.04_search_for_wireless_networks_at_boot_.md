---
title: "Ubuntu 14.04 search for wireless networks at boot delays startup."
date: 2015-12-22
forum: Networking &amp; Wireless
---

### Post by globetrotterdk on 2015-12-22
I have a minimal Ubuntu 14.04 command line install (no GUI) on an Acer laptop. I am using wicd-curses to connect to my wireless network. This works perfectly fine when I login onto my system as a user. Unfortunately at boot, Ubuntu postpones booting processes while looking for a wireless network. This is both frustrating and useless with my configuration. How do I prevent Ubuntu from looking for wireless networks during the boot process?

---

### Post by v3.xx on 2015-12-22
Open up /etc/network/interfaces and edit (hash out) the last two lines.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
[COLOR="#FF0000"]#auto eth0
#iface eth0 inet dhcp[/COLOR]
```

That works for me, but I am not using wicd.  Give it a try :)

---

### Post by globetrotterdk on 2015-12-23
> **v3.xx said:**
> Open up /etc/network/interfaces and edit (hash out) the last two lines.
Cooool. Wow that sucker boots super fast now!

Thanks

---

### Post by v3.xx on 2015-12-23
Welcome :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

