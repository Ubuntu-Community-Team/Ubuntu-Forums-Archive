---
title: "mysql bind internal &amp; external IP"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by sperlyjinx on 2008-02-19
Hi all,

I have mysql running on Ubuntu 7.10 and am able to connect to it from the internal network.  My machine is also accessible via an external IP address, but I cannot connect to the mysql server through this address.  I have removed the bind-address directive from the configuration file, but still have no luck.  I have read that removing this directive will bind mysql to all configured interfaces.  As a note, my external IP address is assigned by a router and there is no explicit configuration for this on my machine.  Is there some way to set up a dummy configuration for this interface so that mysql will bind the address?

Anyone have any similar experience or suggestions?  Let me know if you need any more info for troubleshooting.  Thanks!

-Jay

---

