---
title: "ip config"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by irshan on 2008-05-06
dear friends

i dont know how to look at the ipconfig in ubuntu but in windows if i enter ipconfig in command line it will giv all the information abt if config
so pls help how do i get that information in ubuntu.

---

### Post by tamoneya on 2008-05-06
I think you are looking for this```
ifconfig
```

---

### Post by Aearenda on 2008-05-06
The Linux equivalent is 'ifconfig' - but you also need to do ```
cat /etc/resolv.conf
``` to see the DNS settings, and use 'route' to see the gateway.

---

