---
title: "No network unless IPV 6 is disabled (Resolving host... problem)"
date: 2015-12-13
forum: Networking &amp; Wireless
---

### Post by moma on 2015-12-13
Hello,

I did two installations of Ubuntu, one with Ubuntu 15.10 and other with 16.04 (Xenial test).

Both systems had problems connecting to the net because IPV 6 was enabled.
They could not lookup or resolve the host names.  Resolving host......eternal.

I disabled IP V6 by adding these commands to the /etc/sysctl.conf file.
$ sudo gedit /etc/sysctl.conf

[B]net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1 [/B]

And run:
$ sudo sysctl -p /etc/sysctl.conf

Now the internet is working well.
I still have re-run the sudo sysctl -p command after reboot.

**THIS IS A SHOW-STOPPER FOR NEW USERS WHO DO NOT KNOW COMMAND LINE.**

1) The Ubuntu desktop should have an option to disable IP V6.  Maybe it already has?  
EDIT: I found IP V6 settings in the network-manager. And it has an "ignore" option.

2) Why cannot Ubuntu default to IPV 4 when IPV 6 cannot lookup/resolve the hostname?

My location is: Lisbon / Palmela, Portugal.

Cumprimentos,
  Osmo, Antero

---

### Post by praseodym on 2015-12-13
Please run the wireless-script from the sticky thread for both systems and show the outputs.

---

### Post by moma on 2015-12-13
Ok, I have attached 
 wireless-info-ubuntu1510.tar.gz   and 
wireless-info-ubuntu1604.tar.gz.

Notice: /etc/sysctl.conf is unmodified and IPV6 is set to "Automatic" in the network-manager (this is the default state after installation).

---

### Post by praseodym on 2015-12-13
Did you "ignore" IPv6 in the network-manager settings? Both outputs show "auto" for the respective connection.

---

### Post by moma on 2015-12-14
Thanks for you replies.
No,  I reset the systems to their default values before running the script.

/etc/sysctl.conf was unmodified and IPV6 was set to "Automatic" in the network-manager (this is the default condition after installation). 
I rebooted with these settings, then ran the wireless-script.

Please tell me if you need more tests.

A curiosity:
Some sites, such as [www.google.pt](www.google.pt) functions well and promptly with IP V6 enabled. 
But most of other sites simply timeout with error.

---

### Post by moma on 2015-12-29
Bump.

---

