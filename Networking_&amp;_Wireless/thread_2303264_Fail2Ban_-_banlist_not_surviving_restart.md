---
title: "Fail2Ban - banlist not surviving restart"
date: 2015-11-17
forum: Networking &amp; Wireless
---

### Post by CrimsonRider on 2015-11-17
I've been using Fail2Ban for quite some time now, but I am noticing that on a restart of the Fail2Ban service, the banlist are suddenly empty.
I supposedly parses logs to reinstate bans, but that doesn't seem to be happening. Any idea how to enable this?

---

### Post by TheFu on 2015-11-17
I never had that expectation.  Interesting.  Lets check the manpage.
We only ban for a day.  For permanent bans, we have a list of subnets saved using **iptables-save** or a small perl script for some of the huge lists.  Currently banning about*6700 subnets now.

[https://serverfault.com/questions/192079/permanently-and-persistently-ban-an-ip-with-fail2ban](https://serverfault.com/questions/192079/permanently-and-persistently-ban-an-ip-with-fail2ban)
and
[https://serverfault.com/questions/415040/permanent-block-of-ip-after-n-retries-using-fail2ban](https://serverfault.com/questions/415040/permanent-block-of-ip-after-n-retries-using-fail2ban)

Looks like most people do it a similar way to us.

---

