---
title: "[SOLVED] Change MAC and hostname on the fly"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by victorbrca on 2008-01-08
Hi all,


  I'm trying to change my MAC and hostname on the fly. I'm not really good a scripting. Would the following script work?

```
#!/bin/bash

sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether 00:16:6F:00:00:00
sudo ifconfig eth0 up
sudo hostname <new-hostname>
xauth add <new-hostname>/unix:0  MIT-MAGIC-COOKIE-1 `xauth list | grep <old-hostname> | cut -f5 -d" "`
```

  Would it change to the default after a reboot if I don't make any changes on my /etc/hosts?

Thanks,

Vic.

---

### Post by victorbrca on 2008-01-08
If anyone comes by this, it works, however the entry from .Xauthority does not change after a reboot.

I created 2x files, one to apply the change and another to reset to default (without needing a reboot)

```
#!/bin/bash

sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether <default MAC>
sudo ifconfig eth0 up
sudo hostname <default-hostname>
xauth remove <new-hostname>/unix:0
```

Vic.

---

