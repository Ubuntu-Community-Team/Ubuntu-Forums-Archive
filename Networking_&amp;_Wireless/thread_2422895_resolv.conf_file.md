---
title: "resolv.conf file"
date: 2019-07-14
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2019-07-14
I noticed in my /etc/resolv.conf file that the nameserver is always set to 127.0.0.53, even when I change the DNS option in my isc-dhcp-server config file. Why does it not point to my IP defined in the dhcp conf file?

---

### Post by SeijiSensei on 2019-07-14
[http://manpages.ubuntu.com/manpages/bionic/man8/systemd-resolved.service.8.html](http://manpages.ubuntu.com/manpages/bionic/man8/systemd-resolved.service.8.html)

---

### Post by pcfan1234 on 2019-07-15
In Ubuntu 18.04 and newer it it always a reference to systemd-resolve
You can print out yout DNS with ```
systemd-resolve --status |grep Server 
```

---

