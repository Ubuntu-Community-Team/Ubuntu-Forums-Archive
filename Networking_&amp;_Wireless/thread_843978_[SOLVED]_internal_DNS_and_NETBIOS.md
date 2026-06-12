---
title: "[SOLVED] internal DNS and NETBIOS"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by Nxion on 2008-06-29
Ok, so what I would like to do is whan I do a command like this for example:

```
ping bob
```

(bob = computer on my internal network)

My machine will know what I am talking about and ping it. As it stands right now I have to use IP address all the time. There seems to be no internal DNS resolution. Can anyone steer me in the right direction so I can set it up?

THANKS ALL!

---

### Post by linfidel on 2008-06-29
Add bob to your hosts file.
gksudo gedit /etc/hosts

type 
IP.address    bob

Make sure there is an empty line at the end of the file - press return at the end of the last line.  Otherwise, there may be a problem reading the last line.

---

### Post by Nxion on 2008-07-17
This worked perfectly. Thanks

---

