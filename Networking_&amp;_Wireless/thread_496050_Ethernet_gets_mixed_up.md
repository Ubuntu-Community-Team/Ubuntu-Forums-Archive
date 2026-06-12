---
title: "Ethernet gets mixed up?"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by saxofoner on 2007-07-08
My computer was working fine the other day, at home, on a wired ethernet connection.  I brought it to another house and plugged the ethernet in there and it worked fine there too.  But now, I brought it home, it says it connected, but nothing actually loads.  Windows did the same thing.  (Dual boot)

It's not my router, since this PC works fine.

Any ideas?

---

### Post by aliyanage on 2007-07-08
Hi,

could you post the output of:

```
sudo ifconfig
```

and have you already tried to use this command:

```
sudo dhclient
```


regards
aliyanage

---

