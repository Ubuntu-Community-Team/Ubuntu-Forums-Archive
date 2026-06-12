---
title: "UFW firewall: /etc/sysctl.conf vs. /etc/ufw/sysctl.conf (2)"
date: 2014-12-07
forum: Networking &amp; Wireless
---

### Post by ygoe on 2014-12-07
This thread has been closed, but it was not answered and is still relevant, so I'm asking it again.

[http://ubuntuforums.org/showthread.php?t=2108325](http://ubuntuforums.org/showthread.php?t=2108325)

usually you enable things like IP forwarding in /etc/sysctl.conf. Now I  read through the UFW firewall documentation, and regarding to that, it  has it's own sysctl.conf file in /etc/ufw.

Why is that? What happens if I enable UFW and have things configured in  /etc/sysctl.conf? Will UFW overrule these settings with whatever is in  /etc/ufw/sysctl.conf? Why two files for the same purpose?

Now on 14.04

---

### Post by kevdog on 2014-12-08
I'm not sure if I totally know the answer, however I'm betting the ufw is forwarding or interpreting your setting specified in the firewall and redirecting it to the kernel directive -- like
echo 1 > /proc/sys/net/ipv4/ip_forward

You can do some experimenting, but can always query the status of the kernel ip_forward state by:
cat /proc/sys/net/ipv4/ip_forward

0=forwarding disabled
1=forwarding enabled

---

