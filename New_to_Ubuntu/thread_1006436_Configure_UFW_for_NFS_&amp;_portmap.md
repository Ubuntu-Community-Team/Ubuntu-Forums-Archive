---
title: "Configure UFW for NFS &amp; portmap"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by SpinningAround on 2008-12-09
I'm setting up a NFS server for a local network and would like to configure ufw for this, my question is what are needed for this.

This is what I have atm, I'm unsure but it might even make my system insecure, please help

Port 2049 should be NFS server and 111 portmap
```

192.168.1.33 2049/tcp      ALLOW   192.168.1.35 2049/tcp
192.168.1.33 2049/udp      ALLOW   192.168.1.35 2049/udp
2049/tcp                   DENY    Anywhere
2049/udp                   DENY    Anywhere
192.168.1.35 111/tcp       ALLOW   192.168.1.33 111/tcp
192.168.1.35 111/udp       ALLOW   192.168.1.33 111/udp
192.168.1.33 111/tcp       ALLOW   192.168.1.35 111/tcp
192.168.1.33 111/udp       ALLOW   192.168.1.35 111/udp
192.168.1.35 2049/tcp      ALLOW   192.168.1.33 2049/tcp
192.168.1.35 2049/udp      ALLOW   192.168.1.33 2049/udp
111/tcp                    DENY    111/tcp
111/udp                    DENY    111/udp

```

192.168.1.35 is the server and 192.168.1.33 is the client

---

