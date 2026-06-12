---
title: "Networking problems"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by DeMus on 2008-05-11
Hi,
I have set up Samba on my Ubuntu 8.04 installation.
What works is this:
from Ubuntu I can see shared folders in a Windows machine

What does not work is this:
from the Windows machine I can not see the Ubuntu computer at all. As if it is not connected. So, I not only can not make contact to shared folders, I can not make contact to the computer at all.

Ubuntu has no firewall, Windows firewall is switched of.
Workgroup name is the same in both computers, IP addresses are 192.168.1.52 and .53

Any idea what could be wrong here, please help.

DeMus

---

### Post by rickh57 on 2008-05-11
How are you trying to access the Ubuntu box from the Windows box? Have you tried entering \\192.168.1.52 (or whatever the ip address is of the Linux box) from the run command in Windows? Have you tried pinging the linux box?

---

### Post by DeMus on 2008-05-11
> **rickh57 said:**
> How are you trying to access the Ubuntu box from the Windows box? Have you tried entering \\192.168.1.52 (or whatever the ip address is of the Linux box) from the run command in Windows? Have you tried pinging the linux box?

Yes, I did use the ping command and when I ping directly to the IP-address it works fine. When I use the computername it can not find the host.

Thanks for your ideas, have any more?

---

