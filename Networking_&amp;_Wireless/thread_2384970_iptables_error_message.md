---
title: "iptables error message"
date: 2018-02-14
forum: Networking &amp; Wireless
---

### Post by Cos_Marchy on 2018-02-14
I am trying to setup a openvpn connection to PIA.  Looking at the log file, I can see it is failing with the following error:

```

iptables v1.6.0: can't initialize iptables table `NAT': Table does not exist (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.

```

I have updated and upgraded so I believe I am up to date...

if I do 
```
test@ubuntu:~$ iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination

```
so it looks like I have a nat table...

I've also tried 'nat' and 'NAT', neither of which made any difference.

But, I'm not sure what to do next in order to fix this.  If someone could assist it would be appreciated.

I am using Ubuntu 16.04.03.

Thanks

---

### Post by Doug S on 2018-02-15
> **Cos_Marchy said:**
> I've also tried 'nat' and 'NAT', neither of which made any difference. It is 'nat'

Show us the actual command that is failing.

---

