---
title: "Same Service on Multiple Ports"
date: 2015-05-22
forum: Networking &amp; Wireless
---

### Post by Adam_Kleiner on 2015-05-22
Hello,

I have an Ubuntu server running XRDP on the standard port 3389. I'd like to somehow change this so that XRDP listens on _both_ port 8081 AND port 3389 (exact same service, just offered on two different ports, if that makes sense). Would there be a way to go about this by configuring the XRDP server itself? Or is there some way to go about this in the system firewall?

Also, forgive me if I've posted this in the wrong forum. I'm back after several years away from this forum, and things seem to have changed a LOT!

Thanks!

---

### Post by sandyd on 2015-05-22
Seems like you can only do one port per user:

Ex:
```

[xrdp1]
name=xrdp1
lib=libvnc.so
username=user1
password=ask
ip=127.0.0.1
port=5911

[xrdp2]
name=xrdp2
lib=libvnc.so
username=user2
password=ask
ip=127.0.0.1
port=5912
```

---

### Post by Adam_Kleiner on 2015-05-23
Well, what I mean is how can I offer XRDP *externally* on those two ports? I don't need to change anything about how XRDP talks to the VNC server on the backend. Would there be some way I could somehow configure the system firewall to foward all requests on port 8081 to localhost:3389?

---

