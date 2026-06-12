---
title: "Cannot connect to VPN with Cisco Client"
date: 2006-12-16
forum: Networking &amp; Wireless
---

### Post by kweiner on 2006-12-16
I successfully installed the Cisco VPN client, vpnclient-linux-x86_64-4.8.00.0490-k9, on Ubuntu 6.10, but when I try to connect to the VPN, I get the following error message (IP address is partially masked):

```

Initializing the VPN connection.
Initiating TCP to 66.77.xxx.xxx, port 10000
Contacting the gateway at 66.77.xxx.xxx
Secure VPN Connection terminated locally by the Client
Reason: Remote peer is no longer responding.
There are no new notification messages at this time.

```

The .pcf file I'm using is copied directly from a Windows installation of Cisco VPN client that works without any problems from the same network.

Does Ubuntu block some kind of traffic that is preventing my VPN connection from working?

---

### Post by x64Jimbo on 2006-12-16
try it with sudo.

---

### Post by kweiner on 2006-12-17
> **x64Jimbo said:**
> try it with sudo.

I should have mentioned that I was already running it with sudo:
```
 sudo vpnclient connect work
```

---

### Post by x64Jimbo on 2006-12-17
Ubuntu does not block access by default, but some firewalls could be problematic for you. Have you installed firestarter or something similar?

---

### Post by kweiner on 2006-12-17
> **x64Jimbo said:**
> Ubuntu does not block access by default, but some firewalls could be problematic for you. Have you installed firestarter or something similar?

No, I haven't installed anything firewall related.  I have almost a vanilla Ubuntu 6.10 installation.

---

### Post by x64Jimbo on 2006-12-17
How about connecting without the pcf file? Can you do it step by step? Also, have you tried vpnc (the open source alternative to Cisco's VPN client)?

---

