---
title: "NetworkManager eating up CPU"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by gnychis on 2007-11-25
Hi all,

Ever since I upgraded to Gutsy, NetworkManager has been eating CPU.  It never goes below 10% CPU usage according to top, and will go all the way up to 50% at times.  I have no idea what it's doing... I've rebooted and everything and it still occurs.

Any ideas?

Thanks!
George

---

### Post by spd106 on 2007-11-26
There's a few things you could try.

Use System -> Administration -> System Log to check the syslog for Network Manager errors.

Restart Network Manager via DBus with this command.
```
sudo /etc/dbus-1/event.d/25NetworkManager restart
```

Check the /etc/network/interfaces file for rogue interface definitions. You shouldn't see the names of any interfaces that you want to managed by Network Manager in there, i.e. in roaming mode. This file is really only for static addressing and backwards compatibility.

---

### Post by gnychis on 2007-11-29
> **spd106 said:**
> There's a few things you could try.

Use System -> Administration -> System Log to check the syslog for Network Manager errors.

Restart Network Manager via DBus with this command.
```
sudo /etc/dbus-1/event.d/25NetworkManager restart
```

Check the /etc/network/interfaces file for rogue interface definitions. You shouldn't see the names of any interfaces that you want to managed by Network Manager in there, i.e. in roaming mode. This file is really only for static addressing and backwards compatibility.

bingo, it was an eth0 definition in /etc/network/interfaces that I'm not using.

---

### Post by spd106 on 2007-11-29
[QUOTE=gnychis]bingo, it was an eth0 definition in /etc/network/interfaces that I'm not using.[/QUOTE]
That's good news.

I have a weird issue too, though it's probably hardware related. 

My Cardbus wifi card has a dodgy connector, so sometimes the light goes out and it disappears from the system. This causes Network Manager to go crazy and I end up having to kill the process manually. I think NM could handle this better after all it's supposed to be a hot-pluggable device.

---

