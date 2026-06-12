---
title: "Script to remount shares if sshfs disconnects"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by chadjohnson on 2008-09-11
In case this helps anyone...
```

#!/bin/bash

# Unmount drives as often the system thinks they are mounted, but the SSH
# connection has failed.
fusermount -uz /media/zeus/chad

# If drive is not mounted, (re)mount it.
if ! mount | grep "on /media/zeus/chad type" > /dev/null; then
  mount /media/zeus/chad
fi

```

---

