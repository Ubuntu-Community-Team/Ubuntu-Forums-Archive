---
title: "setting host-identifier through omapi for DCHP server"
date: 2016-12-04
forum: Networking &amp; Wireless
---

### Post by lavalyte on 2016-12-04
We are running an Ubuntu DHCP server and are configuring it from other servers through LDAP, which is turning out to be terrible at the job.
We want to move to omapi.
The problem is, it does not appear to be possible to set the host-identifier on a host through omapi.

We need to set something like;

host AVC000009774999
{ 
    host-identifier option agent.circuit-id "AVC000009774999"; 
}

This works if put in directly to the dhcp.conf file.

The documentation on omshell and omapi has no mention on how or if we can set this.

---

