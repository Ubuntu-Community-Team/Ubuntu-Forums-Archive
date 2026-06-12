---
title: "network-admin segmentation fault in Feisty, a solution."
date: 2007-03-31
forum: Networking &amp; Wireless
---

### Post by Icarosaurus on 2007-03-31
Hi,
I'm using Feisty since its first releases, and for long time I wasn't able to use network administration tool (It wasn't a big problem as I set up network by hand).
Going into System-->Administration-->Network just resulted in a crash.
Writing 
```
sudo network-admin
```
in terminal gave me "segmentation fault (core dumped)"

I found the solution that worked for me here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/86357]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/86357")

In other words I just had to delete the **/root/.gnome2/network-admin-locations** directoy:

```

sudo rm -rf /root/.gnome2/network-admin-locations

```

Hope this can help someone.

---

