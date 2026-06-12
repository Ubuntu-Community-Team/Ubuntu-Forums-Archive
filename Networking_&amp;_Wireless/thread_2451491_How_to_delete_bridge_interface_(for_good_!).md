---
title: "How to delete bridge interface (for good !)"
date: 2020-10-05
forum: Networking &amp; Wireless
---

### Post by kaker on 2020-10-05
hello,

I created days ago a bridge interface br0 for a VM project.
I don't need it anymore and want to delete it.

I use :
```
sudo ip link set br0 down
sudo brctl delbr br0

```

It works but after a reboot br0 is still up !

How to delete it for good ?

Thank you,
Max.

---

### Post by kaker on 2020-10-06
Found it :
```
sudo nmcli connection delete br0


```

---

