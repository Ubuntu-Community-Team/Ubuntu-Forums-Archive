---
title: "Port redirection"
date: 2013-09-28
forum: Networking &amp; Wireless
---

### Post by geohei on 2013-09-28
Hi.

I would like my router (Fritzbox 7390) to port redirect 2 ports from WAN to 1 port LAN (same machine). This apparently doesn't work. It should look like this:
WAN: port 33001/tcp -> LAN: port 39000, machine_1
WAN: port 33002/tcp -> LAN: port 39000, machine_1
The entries are accepted, but port forwarding only takes place on one for one of the 2 ports. I guess it's a bug.

Now ... I try to cirumnavigate this issue by using an Ubuntu 12.04 server which I use inside the LAN where port forwarding takes place. I'd like to use the Ubuntu server to port forward. My idea is this one here:
WAN: port 33001/tcp -> LAN: port 39000, machine_1
WAN: port 33002/tcp -> LAN: port 33002, ubuntu server with port redirection -> LAN: port 39000, machine_1

Is this possible?

Thanks,

---

### Post by gerowen on 2013-09-28
What firmware is your "Fritzbox" running?  Are you managing it via some GUI or via command line?  I'm not promising I'll be able to help, but just gathering some information out of curiosity, and I'll see if I know enough to help in this issue.

---

### Post by geohei on 2013-09-29
05.22. Yes ... I know 5.52 is out but I believe this is a bug which 05.52 doesn't address either. You are free to confirm the behavior ;).
I use GUI to set the port forwardings. However ar7.cfg confirms the settings.

```
# cat /var/flash/ar7.cfg | grep 39000
                                       "tcp 0.0.0.0:33000 192.168.1.77:39000 0 # test1",
                                       "tcp 0.0.0.0:33001 192.168.1.77:39000 0 # test2",
                                       "tcp 0.0.0.0:33002 192.168.1.77:39000 0 # test3";
```

---

