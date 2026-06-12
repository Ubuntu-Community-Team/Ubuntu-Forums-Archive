---
title: "Broke my Connectivity"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by Robotuner on 2007-02-03
Well, I really broke something. I changed a host setting in 
System/Admin/Networking/host tab and then closed the dialog, tested my internet and network connectivity and found I had lost all connectivity.  

Now when I try to open that dialog again, I get a Bug Report prompting me to save the bug report and report it to someone.  I'm thinking that I will need to drop to terminal mode and open a file somewhere to fix this.  

Can someone tell me where and the approximate location within the file to look?

Thanks

---

### Post by gradedcheese on 2007-02-04
The file is /etc/hosts and that contains exactly what appears in the 'hosts' tab.  Mine looks like this (thinky23 is my host name)

```

127.0.0.1 localhost thinky23
127.0.1.1 thinky23

# The following lines are desirable for IPv6 capable hosts

# The following lines are desirable for IPv6 capable hosts
# (added automatically by netbase upgrade)

::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

