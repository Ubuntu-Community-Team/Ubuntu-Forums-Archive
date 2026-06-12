---
title: "find which firewall is active undet Ubuntu 18.04 LTS"
date: 2022-02-27
forum: Networking &amp; Wireless
---

### Post by Krischu on 2022-02-27
How can I find out which firewall is currently active on my Linux server? 

ufw status says "inactive".
iptables -L doesn't list anything relevant.

Doing an nmap shows a selected number of open ports (22, 25, 80 etc.)

EDIT: well, it could be that nmap just shows the situation of all processes offering ports and there isn't any firewall active.

Would it be advisable to add one?  Or would tcp wrapper advisable?

---

### Post by deadflowr on 2022-02-27
> EDIT: well, it could be that nmap just shows the situation of all processes offering ports and there isn't any firewall active.
Well it shows what services are listening,
but yes, while Ubuntu ships with ufw  it's not active until you activate it.
You'd want to set various rules first before activating it as once activated it will cut off those services not set as allowed.
ufw's default activation setup is to deny all incoming, so you'll need to set what to allow and what not to allow before hand,
or else access to those ports and services will be cut off.

See: [https://help.ubuntu.com/community/UFW]("https://help.ubuntu.com/community/UFW")

---

### Post by TheFu on 2022-02-27
There is only 1 firewall. It is part of the Linux kernel.
What you really mean is which firewall interfacing tool is being used?
UFW --> iptables --> Linux filewall.

UFW just makes iptables commands, but it has limited capabilities.
If you need access to everything the kernel firewall can do, use iptables.  It is also fine to use ufw for the easier stuff. Just ensure that your iptables inputs/settings don't conflict.

tcp-wrappers are built-into most network services and have been since the late 1990s. They don't hurt, but if you aren't extremely consistent with how they are configured, then you'll forget they are active for some, but not all daemons. That will cause frustration for yourself when you can't figure out why nothing new works 6 months from now.  Very few people still use tcp-wrappers, especially since inetd/xinetd isn't used anymore, which is how the tcp-wrappers would usually be installed in the 1990s to intercept all inbound connections.

Some other distros have switched from iptables to firewalld. I've only played with it for about 20 minutes. I don't have too much experience with those other distros. Seemed like a clean interface to the kernel firewall.

---

