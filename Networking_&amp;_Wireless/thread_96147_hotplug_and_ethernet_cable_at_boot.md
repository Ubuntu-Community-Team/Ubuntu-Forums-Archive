---
title: "hotplug and ethernet cable at boot"
date: 2005-11-28
forum: Networking &amp; Wireless
---

### Post by joeljkp on 2005-11-28
The presence of this in the /etc/network/interfaces file:

```
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0
```
leads me to believe that it is intended that wired ethernet cables will work in an intelligent fashion - that is, when you plug in the cable, it'll connect, and when you unplug, it'll disconnect.

At boot, it seems that it tries to get a wired connection even when no cable is plugged in, which takes a while and slows down boot time considerably.

Also, when I do plug in a cable after boot, it's detected, but nothing seems to run dhclient.

Thoughts?

---

### Post by spd106 on 2005-11-28
You need to set up an iface entry and have the line auto eth0. have a look at  **$man interfaces**.

example
 
```
iface eth0 dhcp

auto eth0

```
This should have been done for you at setup through the network manager tool,

---

