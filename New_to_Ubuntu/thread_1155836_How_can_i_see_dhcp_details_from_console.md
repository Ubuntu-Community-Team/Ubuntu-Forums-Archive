---
title: "How can i see dhcp details from console?"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by seppl82 on 2009-05-11
Hey,

can somebody tell me how to see details about my currently running dhcp-client?

i've tried ifconfig, but where can i see things like

DHCP lease obtained
DHCP lease expire
Nameserver
DHCP Server

Thanks
/Seppl

---

### Post by Peter09 on 2009-05-11
To get your route tables do

```
route
```

---

### Post by Lampi on 2009-05-11
DHCP lease obtained -> take a look in /var/log/syslog
DHCP lease expire -> take a look in /var/log/syslog
Nameserver -> ?? they are supposed to be listed in /etc/resolv.conf
[...]
DHCP Server -> ??? I have no clue what you'd like to know here, sorry

---

### Post by arapa on 2009-05-11
Check out the file : dhclient.leases

```
man dhclient.leases
```

DESCRIPTION
       The  Internet  Systems  Consortium  DHCP  client keeps a persistent database of leases that it has acquired that are still valid.   The database is a free-form ASCII file containing one
       valid declaration per lease.   If more than one declaration appears for a given lease, the last one in the file is used.   The file is written as a log, so this is not an unusual occurrance.

       The format of the lease declarations is described in dhclient.conf(5).

FILES
       /var/lib/dhcp3/dhclient.leases

---

