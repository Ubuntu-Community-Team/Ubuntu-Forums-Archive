---
title: "Creating Network Namespace without root access"
date: 2014-11-15
forum: Networking &amp; Wireless
---

### Post by stephane8 on 2014-11-15
Hi

I want to create a Network NameSpace using ```
ip netns add NewNetwork
```. However running this command as a user, returns : 
```
mount --make-shared /var/run/netns failed: No such file or directory
```
this requires root acces i.e. using sudo at the beginning of the line.
Is there any way I could create a network namespace without the root priviledge ?

Regards,
Lompik

---

