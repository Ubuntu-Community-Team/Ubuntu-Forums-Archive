---
title: "Unable to do ping between 2 ubuntu hosts"
date: 2019-04-18
forum: Networking &amp; Wireless
---

### Post by rkb83 on 2019-04-18
Hello, 

We have 2 ubuntu VM's one is 18.04 , and the other is 12.04 which are not able to ping each other, we want to SSH between the two for backup purpose but the ping itself is not working between the two. We have static IP's for both the machines and ufw is disabled. Weird thing is we do have other ubuntu machines which can ping and SSH to both these VM's without issues, can someone please guide me on how to troubleshoot this?

---

### Post by TheFu on 2019-04-18
Use IPs.
Show your work.
Check the routing.
Perhaps one is setup with host-only networking?

---

### Post by SeijiSensei on 2019-04-18
Install the traceroute package and run 

```
traceroute ip.of.other.server
```

See where the connection dies, then determine why.

---

