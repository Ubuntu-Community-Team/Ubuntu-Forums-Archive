---
title: "Issues with iptables after configuring fail2ban"
date: 2016-08-09
forum: Networking &amp; Wireless
---

### Post by zoidberg2 on 2016-08-09
I'm running Ubuntu 14.04 as my squid proxy server, I configured iptables to set the default input policy to Deny & to only allow traffic from a specific IP on port 3128 to pass through the firewall and it worked perfectly. I then configured fail2ban & it has rewritten my iptables & it now looks like this, 

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
fail2ban-ssh  tcp  --  anywhere             anywhere             multiport dports ssh

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain fail2ban-ssh (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere           
```


Yet strangely the iptables rules I set earlier to only allow 3128 on specific IP's seems still to be working as I can't connect from IPs that I didn't add to the firewall before setting up fail2ban but when I try & look at my rules I see the policy above which is set to ACCEPT as default. Any ideas as to what's going wrong?

---

