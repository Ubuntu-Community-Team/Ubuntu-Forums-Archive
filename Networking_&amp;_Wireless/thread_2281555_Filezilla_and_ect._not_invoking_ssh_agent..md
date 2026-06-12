---
title: "Filezilla and ect. not invoking ssh agent."
date: 2015-06-07
forum: Networking &amp; Wireless
---

### Post by mccalleyt on 2015-06-07
I am not able to use the public key authentication with filezilla. I have had to resort to running a script at first boot/login to unlock the key for filezilla. I am running Kubuntu 15.04 x86-64. The script looks like this.... 
```

#!/bin/sh
# set SSH_ASKPASS if not set elsewhere
export SSH_ASKPASS=/usr/bin/ssh-askpass
ssh-add </dev/null

```

Anyone have any more permanent fixes for this?

---

