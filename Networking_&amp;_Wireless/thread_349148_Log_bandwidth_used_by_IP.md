---
title: "Log bandwidth used by IP"
date: 2007-01-29
forum: Networking &amp; Wireless
---

### Post by Sirkent on 2007-01-29
I have an Ubuntu server acting as an internet gateway. I'd like to be able to set up some software to log how much internet bandwidth is used by each IP on the network. I've searched for a good way to do this, but I haven't found anything yet.

Could anyone point me in the right direction? Most of the info I've seen on MRTG seems focused on speeds, not total bandwidth and it's definetly not by IP, or even ranged. Other tools measure bandwidth in real time, but again that's not practical.

---

### Post by p!=f on 2007-01-29
These might help
```

apt-cache show ipband bandwidthd

```

---

