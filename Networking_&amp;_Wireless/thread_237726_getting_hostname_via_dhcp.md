---
title: "getting hostname via dhcp"
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by lengs on 2006-08-16
I have a Dapper Drake desktop. I am trying to have the hostname set via dhcp instead of using the one set at installation.

The system manages to get its IP, domain name, and DNS from our DHCP server, but not the hostname.

Has anyone gotten a setup like this to work?
Thanks.

-leng

---

### Post by arkham on 2006-08-16
Are you statically assigning the IP addresses from the DHCP server?

I have done this in the past, the dhcp config looked something like this:

```
host machine1 {
   option host-name "machine1.example.com";
   hardware ethernet 00:00:00:00:00:AA; 
   fixed-address 192.168.100.1;
}
```

It is possible to do this dynamically, though I have never configured such a server myself......

---

