---
title: "DHCP3 Server Exclusions"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by shade6789 on 2008-09-07
I was wondering if anyone knew what I have to put in dhcpd.conf to allow for exclusions for a dhcp pool. I know you can specify a hosts ip by mac like this:

  host test {
      hardware ethernet 08:00:2b:4c:59:23;
     fixed-address 192.168.1.222;
   }

But I would also like to exclude some ip's so they are not used with the set range.  Say my pool is 192.168.1.100 - 192.168.1.254  For example I don't want 192.168.1.131 to be handed out.

Thanks!

---

### Post by kidders on 2008-09-08
Hi there,

Something like this ought to work. (The man page for dhcpd.conf doesn't say you can't use multiple range declarations.)```
subnet 192.168.1.0 netmask 255.255.255.0 {
    ...
    ...
    range 192.168.1.100 192.168.1.130
    range 192.168.1.132 192.168.1.254
    ...
    ...
}
```

---

