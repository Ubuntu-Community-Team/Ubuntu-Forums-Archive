---
title: "WIRED connection doesn't work"
date: 2021-09-29
forum: Networking &amp; Wireless
---

### Post by klundermann on 2021-09-29
For once it's not about wifi, which works fine in my case.  I'm running 20.04.

The command  nmcli  returns the following information about my ethernet:
```

enp2s0: unavailable
           "Realtek RTL8111/8168/8411"
           ethernet (r8169), 78:24:AF:21:95:95, hw, mtu 1500

```

Any ideas on how to activate the wired connection?

---

### Post by linerman on 2021-10-01
Check out that thread
[https://ubuntuforums.org/showthread.php?t=2456227](https://ubuntuforums.org/showthread.php?t=2456227)

I would start from this:
[...]Above of all , the important inconvenience is that sometimes NIC Realtek  is not switching off during reboots. It affects all linux systems if  you have Windows as a parallel installation. 
In such situation : user reboots windows 10 and log into linux, the Ethernet card is switched off and cannot be switched on.
So the user needs to log in again to Windows 10 and shutdown properly the system.
The next step is to wait 2 sec with machine been powered off, and then  run linux. The Ethernet card would be visible and connection would be  established.
That error may be fixed in Windows 10 configuration, but it is not always working. [...]


[URL="https://ubuntuforums.org/showthread.php?t=2456227"]


[/URL]

---

