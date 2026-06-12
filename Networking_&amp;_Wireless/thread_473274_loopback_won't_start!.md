---
title: "loopback won't start?!"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by manifoldronin on 2007-06-13
This is very puzzling - to me.  Over the past couple of days, the loopback interface won't start automatically when the system boots up.  I have to use ifup to manually bring it up.

I didn't make any changes to the network config files. /etc/network/interfaces does still have these lines:
```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

```

The only thing significant over the past couple of days I have done is I moved /var into a separate partition. I did that by entering single user and "cp -a" the entire /var over.  I'm not sure if that would mess up anything?

---

### Post by kevdog on 2007-06-14
Not that it would probably make a difference, but I only have your first 2 lines to reference my lo address and not address, or netmask.

---

