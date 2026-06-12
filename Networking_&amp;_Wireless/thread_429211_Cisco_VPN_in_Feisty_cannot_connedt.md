---
title: "Cisco VPN in Feisty cannot connedt"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by tak1150 on 2007-05-01
I used to be able use this VPN software under Edgy (though I got intermittent disconnection sometimes).

I cannot get it to work under Feisty. Here's the message I get;

```
Cisco Systems VPN Client Version 4.8.00 (0490)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Config file directory: /etc/opt/cisco-vpnclient

Initializing the VPN connection.
Secure VPN Connection terminated locally by the Client
Reason: Failed to establish a VPN connection.
There are no new notification messages at this time.

```

I am using a wireless card ([SIZE="3"]ath0[/SIZE]).

If I try to connect with [SIZE="3"]eth0[/SIZE] (ethernet), then it works.

I am very confused... Could somebody help please!

---

### Post by anzevi on 2007-05-01
You need to disable the eth0 interface first, like this:

```
sudo ifdown eth0
```

After that, you'll be able to connect.
:KS

---

### Post by tak1150 on 2007-05-12
> **anzevi said:**
> You need to disable the eth0 interface first, like this:

```
sudo ifdown eth0
```

After that, you'll be able to connect.
:KS

Thank you! It works! :)

---

