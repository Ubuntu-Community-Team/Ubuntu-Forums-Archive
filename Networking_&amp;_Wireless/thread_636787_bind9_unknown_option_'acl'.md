---
title: "bind9 unknown option 'acl'"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by shashilx on 2007-12-10
When I have in /etc/bind/named.conf.options something like
```
acl "trusted" {
172.16.1.1;127.0.0.1;
};
```

root@shashilx:~# named-checkconf
/etc/bind/named.conf.options:17: unknown option 'acl'

What's wrong?

Ubuntu 7.10

---

### Post by robert_pectol on 2007-12-10
Change it to:
```

acl "trusted" {
   172.16.1.1;
   127.0.0.1;
};

```
or you can do:
```

acl "trusted" {
   { 172.16.1.1; 127.0.0.1; };
};

```
If you want them in the same line.

---

### Post by shashilx on 2008-01-01
in any cases it still tell:

root@shashilx:~# named-checkconf
/etc/bind/named.conf.options:22: unknown option 'acl'

as I understand bind don't know "acl" word??

---

