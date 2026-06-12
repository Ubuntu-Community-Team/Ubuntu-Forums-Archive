---
title: "can't route around XP"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by yosial@gmail.com on 2008-11-26
Hi,

I have XP connected to internet via wireless. XP has built-in ethernet port connected to a hub. Ubuntu system is connected also to this hub via ethernet.

on XP:
    service started - Routing and remote Access

    HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services
       \Tcpip\Parameters        IPEnableRouter is '1'

    Firewall disabled

    ipconfig /all - shows that the host is 
         'IP Routing Enabled - Yes'

    wireless adapter
        ip    192.168.1.100
        subnet    255.255.255.0
        default gateway    192.168.1.1

    ethernet adapter
        ip address    192.168.0.2
        subnet mask    255.255.255.0
        default gateway    192.168.0.29

from the XP both interfaces are pingable
    I can ping 192.168.0.20
    I can ping 192.168.1.1

from ubuntu (eth0) can only the ethernet interface - no routing:
    Can        ping 192.168.0.1
    Can NOT ping 192.168.1.100           ping hangs

from another PC on the wireless network I can ping both interfaces (wireless and ethernet) of the XP router.

Any idea what can cause this?

Thanks a bunch,
Yosi

---

