---
title: "Multiple persistent DNS search domains as DHCP client ?"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by Bel-O-Kan on 2006-12-23
Hello,

I'd like to be able to set several DNS search domains on my Ubuntu 6.06/6.10 clients.
As a DHCP client, I receive the default DNS search domain but I need 3 more domains in order to be able to "know" all needed hosts.

If I add them using the netadmin GUI, I works and all hosts are reachable. /etc/resolv.conf is updated (search entries) but as soon as the lease expires or the client reboots all extra search domains are no more set and I have to set them once again.

How could I set extra **persistent** DNS domains as a DHCP client ?

Thanks a lot in advance, merry Xmas !

---

### Post by tweedledee on 2006-12-23
> **Bel-O-Kan said:**
> How could I set extra **persistent** DNS domains as a DHCP client ?

```
sudo apt-get install resolvconf
sudo gedit /etc/resolvconf/resolv.conf.d/head
```

Add your domains to the end of that file, and they'll automatically be added to resolv.conf each time the file is rewritten.

---

### Post by Bel-O-Kan on 2006-12-24
Thanks a lot tweedledee, you're a star ;)

---

### Post by goobsoft on 2007-03-06
This solution is probably better.

```

aptitude install resolvconf
vi /etc/network/interfaces

```

```

iface eth0 inet dhcp
    dns-search domain.com

```

---

### Post by ericdegen on 2007-05-09
Thanks a bunch goobsoft! this was bothering me on Feisty the last few days.

---

