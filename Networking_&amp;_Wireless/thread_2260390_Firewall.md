---
title: "Firewall"
date: 2015-01-11
forum: Networking &amp; Wireless
---

### Post by MikeMecanic on 2015-01-11
[COLOR=#000000]installed 2 Firewalls after ISO CD installation of 14.04.1 LTS [/COLOR][B].

[https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall)
[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

[B]
Do I need the first one?

Sorry, it¨s written on the page that it¨s installed by default since 8.04LTS.  [/B][/B]

---

### Post by TheFu on 2015-01-12
There is only 1 firewall on Linux. That is iptables (unless you are bleeding edge).  Those programs above are just interfaces on top of iptables. Pick one and use it. Remove the other, if you like.

The kernel devs have been working on a new firewall for Linux that combines many other tools into a single, unified interface. I think it is in the unstable kernels, which Ubuntu shouldn't be using. Sorry, don't remember which kernel version has the newer version. I expect all the end-user firewalls will be updated to work with the new kernel-level firewall once released.

---

