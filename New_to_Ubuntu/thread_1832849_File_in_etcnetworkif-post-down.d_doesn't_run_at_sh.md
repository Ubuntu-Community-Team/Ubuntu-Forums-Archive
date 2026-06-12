---
title: "File in /etc/network/if-post-down.d/ doesn't run at shutdown"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by Frozen Forest on 2011-08-25
After following this guide¹ did I manage to get iptables working except for one thing, the script that should save counters and iptables doesn't run when the computer shutdown or restart.

[https://help.ubuntu.com/community/IptablesHowTo#Solution%20#3%20iptables-persistant](https://help.ubuntu.com/community/IptablesHowTo#Solution%20#3%20iptables-persistant)

---

### Post by sanderd17 on 2011-08-25
can you give the output of the following command? (between CODE tags please)

```

ls -l /etc/network/if-post-down.d/

```

---

### Post by Frozen Forest on 2011-08-30
> **sanderd17 said:**
> can you give the output of the following command? (between CODE tags please)


```

ls -l /etc/network/if-post-down.d/

```

iptablessave
[PHP]
#!/bin/sh
/bin/bash -c "/sbin/iptables-save -c > /etc/iptables.rules"
exit 0
[/PHP]ls -l
```

-rwxr-xr-x 1 root root 77 2011-08-28 18:54 /etc/network/if-post-down.d/iptablessave


```

---

