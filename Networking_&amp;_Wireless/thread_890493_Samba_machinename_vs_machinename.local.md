---
title: "Samba: machinename vs machinename.local"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by sefs on 2008-08-15
Hi all my computer seems to be accessible (read I can ping both machinename and machinename.local) and get a ping reply.

However where samba is concerned, I tend to get better results when browsing and opening shares when using machinename.local.  manchinename on the other hand tends to give errors.

However it seems by default samba sets up the shares to use machinename as opposed to machinename.local. So you usually have to type in manually smb://manchinename.local in the path bar to get any success.

Whats the story behind machinename and machinename.local and how do I get this all straightened out so that probably machinename.local is used by default, since it seems to work better when this name is used?

Thanks.

---

### Post by Iowan on 2008-08-15
Out of curiosity, what's in your **/etc/hosts** file?

---

### Post by sefs on 2008-08-16
Hi there ...

Here is what I see in there ...

```

127.0.0.1       localhost
127.0.1.1       machinename

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

> **Iowan said:**
> Out of curiosity, what's in your **/etc/hosts** file?

---

