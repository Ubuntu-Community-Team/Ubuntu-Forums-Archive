---
title: "dist-upgraded 6.10 to 7.04, /etc/network/interfaces now ignored"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by dittoalex on 2007-08-17
Upgraded using cli, restarted, and now eth0 doesn't dhcp on startup, I have to do it manually.

**cat /etc/network/interfaces**
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
        hwaddress ether xxxxxxxxxx
```

**/etc/init.d/networking restart** gives
```
 * Reconfiguring network interfaces...
SIOCSIFHWADDR: Device or resource busy
Failed to bring up eth0.
   ...done.

```

I can bring eth0 down/up with ifconfig.  :popcorn:

---

