---
title: "can't edit/disable auto eth0/1 permanently"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by hachel on 2008-10-31
hi there,
I got the two connections for my two adapters, eth0 and eth1 (auto-). I got my cable plugged into eth0, so I would set ip4 with eth0 to manual and enter my ip, dns etc, and delete auto eth1.
Internet works from that point on, but when i restart ubuntu eth1 is back and eth0 is set to the defaults again (automatic dhcp).
I tried adding a new connection and that new connection actually survives the reboot and connects, but only after like 10 seconds or so. Until then the network-icon in the top-right-corner changes to a rotating icon. When i hover that icon it tells me that it's trying to get a network address (or something like that), which i think has to do with the 2 auto eths trying to connect via automatic dhcp.

any help?

cheers,
hachel

---

### Post by francisc1701 on 2008-10-31
If it survives reboot and connects what's the problem? 10 seconds isn't the end of the world :)

---

### Post by hachel on 2008-10-31
well it's more 20 than 10 seconds and conky can't update the weather on startup without internet.
Also, this never happened with 8.04 and whats the point of the two connections if you cant do nothing with it?

---

### Post by Iowan on 2008-10-31
Did you edit the changes into */etc/network/interfaces*?

---

### Post by hachel on 2008-10-31
hi,
there is not that much to edit:
```
auto lo
iface lo inet loopback
```

---

### Post by cariboo on 2008-10-31
This is a bug in network manager, see this:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/283233](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/283233)

It says it has been triaged, so we should see a fix fairly soon.

Jim

---

