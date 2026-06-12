---
title: "Where are the iptables chains in the /proc fs?"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by hellospencer on 2006-10-11
Hello,

I want to write a script that automatically empties all chains and removes all not standard chains. For this I need to build a list of all available chains. 

Can the chains be found in the /proc filesystem?

Cheers A.

---

### Post by hellospencer on 2006-10-11
Well I'm using now:

CHAINS=`iptables -L | grep -e "Chain" | awk '{print $2}'`

But nevertheless, please let me know what's the relation between the chains and the /proc.

---

