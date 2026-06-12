---
title: "Local computer names have to end with .local"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by josteinaj on 2008-05-31
I've got three Ubuntu computers (my laptop, my desktop and my server) in my home network. There's also a couple of windows machines in the network.

Previously, when connecting to one pc from another, for instance using ssh in gnome-terminal, this would do the trick:
```
ssh computername
```

However, after upgrading from Ubuntu 7.10 to 8.04, I have to do this:
```
ssh computername.local
```

I believe the problem started when I upgraded Ubuntu, but I also changed my router about the same time - maybe a little earlier. I don't remember the name of the old router, but this one is Jensen Airlink 2954.

---

