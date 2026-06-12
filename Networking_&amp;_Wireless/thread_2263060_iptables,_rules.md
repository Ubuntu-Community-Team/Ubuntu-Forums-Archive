---
title: "iptables, rules"
date: 2015-01-29
forum: Networking &amp; Wireless
---

### Post by liviusbr on 2015-01-29
Hi all,

Just wondering what this rule is exactly doing :

-A INPUT -d 10.244.39.33/32 -i bond1.2017 -p tcp -m tcp --dport 22 -m state --state NEW,ESTABLISHED -m comment --comment "allow ssh requests" -j ACCEPT



To my understanding if I apply the rule on the INPUT, I should specify -s (from which source) I allow or deny.
This rule, nevertheless, specifies -d (destination). for me it is confusing .
Anyone can explain what that does ?

Regards,
Liviu Sisu

---

### Post by TheFu on 2015-01-29
I thnik it allows ssh into 1 ip from anywhere.

---

### Post by SeijiSensei on 2015-01-29
Excluding the source address tells iptables to use its default which is 0.0.0.0/0, or as the TheFu observes, all other machines.

If you display the rules with "sudo iptables -L -nv" you'll see that ones without a specified input or output address will have 0.0.0.0/0 in the report.

---

