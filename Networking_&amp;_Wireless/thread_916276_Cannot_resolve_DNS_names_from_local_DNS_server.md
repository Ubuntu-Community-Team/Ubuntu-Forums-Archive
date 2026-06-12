---
title: "Cannot resolve DNS names from local DNS server"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by eggy524 on 2008-09-10
Hi there,

I'm running pfsense as a firewall and using it as a DNS forwarder for domain names. E.g. router.local goes to 192.168.1.50 etc.

These dns names work in windows but since I have moved to ubuntu i cant seem to get any to work.

I've searched around the forums and tried a few things but none of the solutions offered seem to make any difference.

Anyone have any ideas?

Thanks

---

### Post by Iowan on 2008-09-11
What's in **/etc/resolv.conf**?

---

### Post by eggy524 on 2008-09-11
contents of resolv.conf:

```
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5318
#
### END INFO

search local


nameserver 192.168.1.1
```

What is strange is that if i change my firewall to have a .lol domain it works e.g. pfsense.lol works instead of pfsense.local

For some reason my ubuntu box just doesnt like .local domains

thanks for your help, any more ideas?

---

### Post by Iowan on 2008-09-11
Grasping at straws, a bit... 
I doubt **.local** or just plain "." will work...
I didn't see any absolute answers in **man resolv.conf**

---

