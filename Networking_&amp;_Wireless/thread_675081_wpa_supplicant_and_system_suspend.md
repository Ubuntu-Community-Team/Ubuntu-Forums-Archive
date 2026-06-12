---
title: "wpa_supplicant and system suspend?"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by EricDB on 2008-01-22
I've managed to get Ubuntu 7.10 to connect to my university (of Iowa) wireless network.  I use this script:

```
#!/bin/sh
wpa_supplicant -Dwext -ieth1 -c/etc/wpa_supplicant.conf &
dhclient eth1
```

That works fine.  As an aside (or, maybe it's the whole answer here), I'd like to know where to put these commands so that I don't have to run "sudo ./netcon" every time I start my computer.

The main problem, though, is that after waking from suspend, the script doesn't work--it loops forever in DHCP discovery.  I think some processes are still running, but I don't know which to look for or how to fix it.  Restarting the computer and running the netcon script above enables me to reconnect, but obviously that's not a long-term solution.

I'll be glad to provide any information that might help diagnose this.  Thanks!

---

### Post by EricDB on 2008-01-25
I figured out something that works...in case anyone else is having this problem (or would care to comment on my solution--I doubt it's the "proper" one), here's what helped...I added two lines to my netcon script to clear out a couple of files that seemed to be causing trouble:

```
#!/bin/sh
rm /var/run/wpa_supplicant/eth1
rm /var/run/dhclient.pid
wpa_supplicant -Dwext -ieth1 -c/etc/wpa_supplicant.conf &
dhclient eth1
```

---

