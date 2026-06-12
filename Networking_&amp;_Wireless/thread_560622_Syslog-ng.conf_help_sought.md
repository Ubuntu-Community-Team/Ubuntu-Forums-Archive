---
title: "Syslog-ng.conf help sought"
date: 2007-09-26
forum: Networking &amp; Wireless
---

### Post by Hase on 2007-09-26
Trying to source by IP but I keep getting errors.

```
options {
        sync (0);
        log_fifo_size (2048);
        create_dirs (yes);
        group (logs);
        dir_group (logs);
        perm (0640);
        dir_perm (0750);
};

source s_gateway01 { udp(ip("10.11.10.1")); };

destination d_gateway { file("/var/log/$YEAR/$MONTH/$YEAR$MONTH$DAY-gateway-$HOST.log"); };

log { source(s_gateway01); destination(d_gateway); };

```

I get:
```
Error binding socket; addr='AF_INET(10.11.10.1:514)', error='Cannot assign requested address (99)'
Error initializing source driver; source='s_gateway01'
```

Any ideas?

---

