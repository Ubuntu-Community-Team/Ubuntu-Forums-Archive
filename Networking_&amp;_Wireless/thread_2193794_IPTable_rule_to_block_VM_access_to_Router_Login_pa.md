---
title: "IPTable rule to block VM access to Router Login page"
date: 2013-12-14
forum: Networking &amp; Wireless
---

### Post by senrabdet on 2013-12-14
Hi All:

I am running virtual machines on an Ubuntu Host (10.4).  The VMs run Gnome and have browsers that can reach the Internet.  The VMs are on a subnet.  For the sake of argument, the VMs are on 192.168.0.X/24 and the host is on 192.168.5.X/24.  Right now, the VMs via their browsers can reach the router/firewall login page, which I would like to prevent while leaving them the ability to get to the Internet.

Q:  Is there an IPTable rule (or one in ufw) someone could suggest that:
a)  would prevent the virtual machines from reaching the router login page (on the same subnet as the host) and
b) still allow VM browser access to the Internet

Any help appreciated!

Thanks!

---

### Post by CharlesA on 2013-12-14
The rule would depend on what port the router software is listening for connections. Assuming it is port 80, you can just tell iptables to block outgoing access to that IP address on port 80, but this will also mess with internet access.

Your best bet is it just leave it alone. The router/firewall settings are behind a login screen, right?

---

### Post by senrabdet on 2013-12-15
Thanks CharlesA - yes, it's behind a strong password.  Would prefer not to give people access to login screen at all...but need to give access to Internet.  Thanks for giving this a think...

---

### Post by SeijiSensei on 2013-12-15
```
/sbin/iptables -I INPUT -d ip.of.the.router -j REJECT
/sbin/iptables -I INPUT -s ip.of.your.machine -d ip.of.the.router -j ACCEPT
```

These two rules will be "inserted" (-I) at the top of the iptables ruleset.  They appear in reverse order.

Once entered, you will be able to access the router from ip.of.your.machine but not from anywhere else.

---

