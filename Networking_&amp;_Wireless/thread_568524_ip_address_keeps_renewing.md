---
title: "ip address keeps renewing"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by akshunj on 2007-10-05
My IP address on my Feisty media server keeps renewing even though my router has asigned it a static address.  Makes broadcatching bittorrents a bit....... challenging.

I have just tried killing the dhclient process to see if that will fix the issue, based on a suggestion in a similar post.  We'll see if this works.  And other suggestions?  Thanks!

--Akshun J

---

### Post by noob12 on 2007-10-06
Can you post the output of these
```

cat /etc/network/interfaces

ls /var/lib/dhcp3/

```

---

### Post by akshunj on 2007-10-10
So, killing the dhclient process fixed the issue.

---

