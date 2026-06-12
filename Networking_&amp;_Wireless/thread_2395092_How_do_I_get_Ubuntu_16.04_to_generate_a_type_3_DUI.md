---
title: "How do I get Ubuntu 16.04 to generate a type 3 DUID instead of a Type 1 DUID?"
date: 2018-06-26
forum: Networking &amp; Wireless
---

### Post by meganthetechy on 2018-06-26
I'm trying to get IPv6 set up on a client (minimal install, no GUI) using DHCPv6. It appears that Ubuntu by default configures dhclient to generate a Type 1 DUID (LLT) - an ID based on the mac address and the time of boot.


  Instead I'd like it to generate a Type 3 DUID (LL) - an ID based  purely on the MAC address. This will create a static DUID which I can  then use to get the DHCPv6 server to send client-specific configuration.


  I have been unable however to trace through where Ubuntu calls dhclient to pass in the -D argument to tell it to generate a Type 3 DUID. From what I can tell systemd calls out to the ifup@.service script, but I can't find where abouts in that script, or the scripts it calls out to, dhclient is called.

So... how can I get it to generate a type3 DUID?

Thanks!

---

