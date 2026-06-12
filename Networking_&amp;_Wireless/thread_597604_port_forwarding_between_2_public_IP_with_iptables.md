---
title: "port forwarding between 2 public IP with iptables?"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by mulysa on 2007-10-30
Refering to the discussion here [http://communities.vmware.com/message/782762#782762](http://communities.vmware.com/message/782762#782762)
This guy got the same problem as mine.

What I am going to do is 

I am going to implement a VM which behave as honey pot.

Now I want to do as following:

Redirect all incoming traffics to IP A, port X ---> IP B, port X.

but I don't expertise with iptables, any one know how to do that?
I have tried following cmd as shown below and it doesn't work:
```

root@hpot:~# iptables -t nat -A PREROUTING -p TCP -d MYIP_A --dport 443 -j DNAT --to-destination MYIP_B:22
root@hpot:~# iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target prot opt source destination
DNAT tcp -- anywhere MYIP_A tcp dpt:https to:MYIP_A:22

Chain POSTROUTING (policy ACCEPT)
target prot opt source destination

Chain OUTPUT (policy ACCEPT)
target prot opt source destination


```

Then I tried the following cmd
```

root@hpot:~# ssh MYIP_A -p 443

```


The result was  that it freezed not responde anything back

Note:
MYIP_A = public ip of server A
MYIP_B = public ip of server B

---

### Post by mulysa on 2007-10-31
Bump

---

