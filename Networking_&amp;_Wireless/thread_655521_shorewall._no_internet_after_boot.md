---
title: "shorewall. no internet after boot"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by ezacon on 2008-01-01
From last upgrade from 7.04 to 7.10, my Linux firewall based on Shorewall does not work after boot.
My shorewall server has 2 nic (lan and wan). After reboot, there is no internet access from lan. The internet access is restored after clearing and starting shorewall. A shorewall restart does not work.
Does anyone had same problem?

---

### Post by andguent on 2008-01-25
I realize this post is a few weeks old, so I'm hoping you figured out your problem by now. Is it still giving you problems?

If you are still having problems, can you run the following commands and post the output?

find /etc/rc*|grep shorewall
cat /etc/default/shorewall

I assume that the command 'shorewall check' completes find with a line at the end similar to "Shorewall configuration verified"?

---

