---
title: "flakey zeroconf name resolution"
date: 2005-11-08
forum: Networking &amp; Wireless
---

### Post by ssam on 2005-11-08
i have two computers running breezy. one is a headless jukebox, the other a laptop

they both have avahi and libnss-mdns installed, and are wirelessly networked.

from the laptop i can do

```
ssh -CX jukebox.local
```

to log in to the jukebox. but after a few hours the remote shell will freeze up.

when i try to log in again i get the message

```
ssh: jukebox.local: Name or service not known
```

if i run

```
sudo /etc/init.d/avahi-daemon restart
```

then it works again.

```
ps aux | grep avahi
```

shows that the daemon had not died (run before restarting avahi).

i'd like to report a bug, but it does not seem specific enough yet. any ideas where i could get somemore info about what is going on? log files maybe?

sam

---

