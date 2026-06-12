---
title: "Installed Server minimal - now waits for network configuration"
date: 2014-11-28
forum: Networking &amp; Wireless
---

### Post by bizres on 2014-11-28
Hi,

I did a clean install of Ubuntu server 14.04 minimal on my machine.

During the setup it detected and automatically configured DHCP, then when the setp completed and the system rebooted, the message "waiting for network configuration..." came up and finally the system started without any network config.

Now when I do things like **$ sudo ifdown eth0** it just ends up in```
ifdown: interface eth0 not configured
```

Would really appreciate some help on this, pls.

Thanks in anticipation.

---

### Post by DigiAngel on 2014-11-28
What does"

```
sudo ifconfig -a
dmesg | grep eth
```

Show?

---

### Post by bizres on 2014-11-28
> **DigiAngel said:**
> What does"

```
sudo ifconfig -a
Just took a snaphot to avoid any typos;)
[IMG]http://www.africadreamholidays.com/images/ifconfig.jpg[/IMG]

> **DigiAngel said:**
> dmesg | grep eth
```
```
~$ dmesg | grep eth
[    0.900207] r8169 0000:02:00.0 [COLOR="#FF0000"]eth[/COLOR]0: RTL8168b/8111b at 0xffffc90010724000, 00:25:11:49:52:e2, XID 18000000 IRQ 42
[    0.900209] r8169 0000:02:00.0 [COLOR="#FF0000"]eth[/COLOR]0 jumbo features [frames:4080 bytes, tx checksumming: ko]
[    9.620812] IPv6: ADDRCONF(NETDEV_UP): [COLOR="#FF0000"]eth[/COLOR]0: link is not ready
```

---

### Post by slickymaster on 2014-11-28
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by DigiAngel on 2014-11-28
Looks like your /etc/network/interfaces doesn't have the right info...something like:

```
auto eth0
iface eth0 inet dhcp
```

---

### Post by bizres on 2014-11-29
> **DigiAngel said:**
> Looks like your /etc/network/interfaces doesn't have the right info...something like:

```
auto eth0
iface eth0 inet dhcp
```

Thanks DigiAngel.
It worked.

For some reason the interfaces file was set to p4p1 instead of eth0
Changed it and all's good:D

---

