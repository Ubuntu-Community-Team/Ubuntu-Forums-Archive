---
title: "Interface eth on 14.04.3"
date: 2016-01-10
forum: Networking &amp; Wireless
---

### Post by davaweb on 2016-01-10
Hi,
14.04.3 and 14.04.2

I have been confused for some time why my 14.04.3 installation only has eth1 but 14.04.2 has eth0.

This morning I did new installs of both and attach screenshots of ifconfig.

Does it matter if 14.04.3 calls it eth1? Are there any security or openvpn issues by not having eth0?

Many thanks,
David

---

### Post by ajgreeny on 2016-01-11
Is this two installations on one machine or two separate computers; the hardware address suggests you have just one computer?

The simple answer is that normally it does not matter too much how it is numbered as long as you use the correct naming when configuring the connection manually, should you need to do that. Mostly, ethernet just works, so very little configuring is needed by manually editing config files.

---

### Post by davaweb on 2016-01-11
It is one machine - 4 hard drives. Only one hard drive is on at a time. So each install thinks it is the only disk in the system.

I have seen a lot of posts on the net telling people how to change eth1 to eth0 so I wondered, in a one NIC system, why this would be necessary.

---

