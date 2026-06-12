---
title: "How to repair an IP connection"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by teachop on 2007-05-08
What is the equivalent of the "repair" tcpip operation in Windows?  The reason I ask is that sometimes, rarely, my laptop seems to forget its IP address coming out of suspend.  It is Feisty on an Acer with built-in Atheros wireless, and Network Manager is disabled because it would not stay connected for 5 minutes in a row.

---

### Post by heimo on 2007-05-08
> **teachop said:**
> What is the equivalent of the "repair" tcpip operation in Windows?

What does it do? I'd guess:

```
sudo dhclient eth0
```

---

### Post by chili555 on 2007-05-08
```
sudo ifdown ath1
sudo ifup ath1
```Substitute your wireless interface here, if it's not ath1.

---

### Post by teachop on 2007-05-08
Thanks, that was quick and just what I needed.

---

