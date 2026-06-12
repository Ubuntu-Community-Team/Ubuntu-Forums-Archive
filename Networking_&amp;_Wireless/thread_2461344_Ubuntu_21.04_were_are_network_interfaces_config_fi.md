---
title: "Ubuntu 21.04: were are network interfaces config files?"
date: 2021-04-28
forum: Networking &amp; Wireless
---

### Post by gaetan-quentin on 2021-04-28
Hi, i am a bit lost.

Network works perfectly but i need to add interfaces:  vlan, dummy interfaces, bridges etc ...

/etc/netplan says NetworkManager do all the taff
/etc/network/interfaces does not exist...

I have enp** interfaces but grep  -ri enp /etc/ gives nothing.

So what should i do to add bridges, dummy interfaces and others?

With 20.04 i have uninstalled netplan, installed ifupdown scripts and set /etc/network/interfaces.d files.


Regards.
Gaetan

---

### Post by chili555 on 2021-04-28
> So what should i do to add bridges, dummy interfaces and others?I suggest that you reinstall netplan and disable Network Manager.

You may find example templates at /usr/share/doc/netplan/examples/.

---

