---
title: "determine time to dhcp lease up?"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by not_a_commie on 2007-05-03
Can somebody tell me how to determine how much time is left on my dhcp lease in edgy? Thanks. After searching the web, I tried "netstat -D" and "ifconfig eth0 dhcp status" with no luck.

---

### Post by lloyd_b on 2007-05-03
Try "cat /etc/dhcp3/dhclient.leases".  This file stores in the info on what leases have been obtained, and should specify when they expire.

Lloyd B.

---

### Post by Sendervictorius on 2007-05-03
This one way I think works. Its feisty (which is probably the same as edgy).

Look in /var/lib/dhcp3. There should be a file for each dhcp interface. Mine is dhclient.ath0.leases

the contents of the file gives you dhcp information. Mine looks like this:

```
lease {
  interface "ath0";
  fixed-address 192.168.0.145;
  option subnet-mask 255.255.255.0;
  option dhcp-lease-time 604800;
  option routers 192.168.0.1;
  option dhcp-message-type 5;
  option domain-name-servers 203.96.152.4,192.168.0.1;
  option dhcp-server-identifier 192.168.0.1;
  option dhcp-renewal-time 604780;
  option dhcp-rebinding-time 604780;
  renew 3 2007/5/9 14:23:35;
  rebind 4 2007/5/10 06:41:23;
  expire 4 2007/5/10 06:41:43;
}
```

Showing when the lease will expire

---

