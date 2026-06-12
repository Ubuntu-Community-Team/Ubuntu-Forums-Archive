---
title: "cisco - VPN Connection Faild"
date: 2015-06-24
forum: Networking &amp; Wireless
---

### Post by mohammad16 on 2015-06-24
Hi
Why is Cisco AnyConnect VPN not working?
A screenshot of my config is attached.

[http://i.stack.imgur.com/VfCPn.png](http://i.stack.imgur.com/VfCPn.png)

[http://i.stack.imgur.com/p5SYS.png](http://i.stack.imgur.com/p5SYS.png)
[http://i.stack.imgur.com/e71kS.png](http://i.stack.imgur.com/e71kS.png)


  [http://i.stack.imgur.com/IrcFQ.png](http://i.stack.imgur.com/IrcFQ.png)
  [http://i.stack.imgur.com/8QcKs.png](http://i.stack.imgur.com/8QcKs.png)

---

### Post by sandyd on 2015-06-25
Please post the output of
```

cat /var/log/syslog | grep NetworkManager
``` after attempting to connect

---

### Post by mohammad16 on 2015-06-25
Tnx sandyd


```
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: <info> Starting VPN service 'vpnc'...
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: <info> VPN service 'vpnc' started (org.freedesktop.NetworkManager.vpnc), PID 5232
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: <info> VPN service 'vpnc' appeared; activating connections
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: <info> VPN connection 'us1.cisc.taktafil.in' (ConnectInteractive) reply received.
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: <info> VPN plugin state changed: starting (3)
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: ** Message: vpnc started with pid 5238
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: <info> VPN connection 'us1.cisc.taktafil.in' (Connect) reply received.
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: /usr/sbin/vpnc: option 'IPSec ID' requires a value!
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: /usr/sbin/vpnc: missing IPSec secret
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: ** (nm-vpnc-service:5232): WARNING **: vpnc exited with error code 1
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: <warn> VPN plugin failed: connect-failed (1)
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: <info> VPN plugin state changed: stopped (6)
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: <info> VPN plugin state change reason: unknown (0)
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
```

---

### Post by sandyd on 2015-06-26
> **mohammad16 said:**
> Tnx sandyd

```

Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: <info> Starting VPN service 'vpnc'...
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: <info> VPN service 'vpnc' started (org.freedesktop.NetworkManager.vpnc), PID 5232
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: <info> VPN service 'vpnc' appeared; activating connections
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: <info> VPN connection 'us1.cisc.taktafil.in' (ConnectInteractive) reply received.
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: <info> VPN plugin state changed: starting (3)
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: ** Message: vpnc started with pid 5238
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: <info> VPN connection 'us1.cisc.taktafil.in' (Connect) reply received.
[B]Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: /usr/sbin/vpnc: option 'IPSec ID' requires a value!
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: /usr/sbin/vpnc: missing IPSec secret[/B]
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: ** (nm-vpnc-service:5232): WARNING **: vpnc exited with error code 1
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: <warn> VPN plugin failed: connect-failed (1)
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: <info> VPN plugin state changed: stopped (6)
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: <info> VPN plugin state change reason: unknown (0)
Jun 26 02:02:49 Iran-Ersal-Notebook NetworkManager[783]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
```

Likely requires group username/password

---

### Post by wildmanne39 on 2015-06-27
*Thread moved to **Desktop Environments**.*

Please use thumbnails or url's when posting images because many people have slow connections or a limit on bandwidth.
Thanks

---

