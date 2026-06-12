---
title: "problem mounting nfs share when offline"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by tr3s on 2008-07-23
hi! i was able to mount a nfs share from the server to 50 client computers. this is what i have

```
in /etc/exports:

/files 192.168.0.0/24(rw,no_root_squash,async)
```

but i noticed that everytime my internet connection is down, i can mount the nfs share to a maximum of 4 client computers only and takes a long time to mount. what could be the reason for this?

it really makes my head spinning cause when the connection is up, then nfs works perfectly.

btw, internet connection is shared through a proxy server and nfs server is installed in a separate computer.

tnx in advance

edit: sorry folks, but this should be posted at the servers section

---

