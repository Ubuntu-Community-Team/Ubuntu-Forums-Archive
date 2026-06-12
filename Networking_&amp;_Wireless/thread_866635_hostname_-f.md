---
title: "hostname -f"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by jimbo99 on 2008-07-22
I can't get hostname -f to report anything other than unknown host

Anyone know what's wrong?

the /etc/hosts file is as follows:

127.0.0.1 localhost.localdomain localhost
192.168.0.117 theone


In System > Administration > Networking

After Unlocking and selecting "General"

theone is listed as the hostname





If I type hostname and hit enter it says:

theone


If I type hostname -f and hit enter it says:

Unknown host


The difference is HUGELY important and I have to be able to get hostname -f to report back the proper fully qualified hostname.

Any help would be greatly appreciated.  Only I need the help immediately.

---

### Post by Oldsoldier2003 on 2008-07-22
tryreplacing
```
127.0.0.1 localhost.localdomain localhost
```
with

```
 127.0.0.1 theone
```

---

### Post by Bachstelze on 2008-07-22
> **jimbo99 said:**
> 
The difference is HUGELY important and I have to be able to get hostname -f to report back the proper fully qualified hostname.

set in in /etc/hostname, and with [i]hostname host.domain[/code].

---

