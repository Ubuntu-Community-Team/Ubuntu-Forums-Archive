---
title: "iptables-save problem at 14.04"
date: 2016-02-27
forum: Networking &amp; Wireless
---

### Post by secoonder on 2016-02-27
Hello
i am using iptables at ubuntu 14.04.4 Trusty
When i changed one rule at iptables,the rule was not active.
i installed iptables-persistent.
When i changed one rule at iptables,i saved the rule this command
**#iptables-save > /etc/iptables/rules.v4**
the rule was not active again.And i add the command
**#invoke-rc.d iptables-persistent save**
* Saving rules. . .
* ipv4. . . 
* ipv6. . .
But the rule was not active again.

But when i reboot the server,the rule is active.
Can you help me ?Thank you

---

### Post by blueridgedog on 2016-02-28
I have not used iptables manually in a long time, but when I did, I had to add a rule, restart the process and then test the rule.  I suggest you restart iptables after you make a rule change.

---

### Post by secoonder on 2016-03-03
blueridge thank you.
i am doing it now me too.i agree with you that's better choice.thank you

---

