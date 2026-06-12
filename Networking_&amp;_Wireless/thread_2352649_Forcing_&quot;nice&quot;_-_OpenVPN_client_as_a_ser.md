---
title: "Forcing &quot;nice&quot; - OpenVPN client as a service"
date: 2017-02-14
forum: Networking &amp; Wireless
---

### Post by m-dw on 2017-02-14
Hi

I've added the following directives to my openVPN client configuration file in order to maximise the VPN throughput on my Ubuntu 16.04 based VPN router/gateway.

```

fast-io
nice -20

```
Starting my VPN with sudo service openvpn restart, initiates the VPN correctly, but the "nice" directive isn't applied. Relavent lines of log are below.

```

Feb 14 12:30:09 srvbuntu ovpn-airvpn[23065]:   nice = -20
...
Feb 14 12:30:09 srvbuntu ovpn-airvpn[23065]:   fast_io = ENABLED
...
Feb 14 12:30:09 srvbuntu ovpn-airvpn[23067]: WARNING: nice -20 failed: Operation not permitted: Operation not permitted (errno=1)

```

If I start the VPN from the CLI using "sudo openvpn airvpn.conf" the "nice" directive is implemented:
```

Tue Feb 14 12:37:25 2017 us=588423 nice -20 succeeded

```

What is preventing the nice directive from being followed?

---

### Post by m-dw on 2017-02-16
Found it:

[COLOR=#282828][FONT=Proxima-Nova]For systems using systemd, you set capabilities for an openvpn connection in /usr/lib/systemd/system/openvpn@.service. I achieved what I needed to by adding " CAP_SYS_NICE" to the line beginning "CapabilityBoundingSet="[/FONT][/COLOR]

---

