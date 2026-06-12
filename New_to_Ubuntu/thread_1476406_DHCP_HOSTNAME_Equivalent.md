---
title: "DHCP_HOSTNAME Equivalent"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by john.hall on 2010-05-07
In Ubuntu, what is the equivalent of setting DHCP_HOSTNAME in /etc/sysconfig/network and /etc/sysconfig/network-scripts/ifcfg-eth0 in RHE?  The hostname needs to be updated in DNS.

I'm running Turnkey's 9.10 LAMP Virtual Appliance using VMware Server.

---

### Post by cariboo on 2010-05-08
/etc/hosts ?

---

### Post by Iowan on 2010-05-08
*/etc/hostname*? There's also an option in */etc/dhcp3/dhclient.conf* to ```
send host-name "<hostname>";
```

---

