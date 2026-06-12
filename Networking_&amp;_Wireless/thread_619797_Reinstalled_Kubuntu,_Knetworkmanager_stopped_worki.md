---
title: "Reinstalled Kubuntu, Knetworkmanager stopped working"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by Auax on 2007-11-21
I got tired of not having WINE in 64 bit, so I reinstalled Kubuntu 32 bit on my laptop. However, now Knetworkmanager's interface says "No active devices" when the configuration says my wireless card is active and has recieved an IP from dhcp.

---

### Post by wieman01 on 2007-11-22
Please do this:
> sudo kate /etc/network/interfaces
Then replace(!) the contents with:
> auto lo
iface lo inet loopback
Now reboot the PC and see if you can connect.

---

### Post by Auax on 2007-11-22
Thanks! That worked!

Can you explain to me what that does though, so I know what's going on?

---

### Post by wieman01 on 2007-11-22
> **Auax said:**
> Thanks! That worked!

Can you explain to me what that does though, so I know what's going on?
In older versions of Ubuntu NM you had to remove all interface lines from that file. Then somehow mysteriously NM would ignore them in later versions so that it would work without entirely removing them. But as of late, something has changed and NM no longer works or would pick up the interface while there is still a reference in "/etc/network/interfaces". Don't ask me why, I simply think that's yet another bug... a very annoying one.

---

### Post by jaceituno on 2008-06-14
> **wieman01 said:**
> In older versions of Ubuntu NM you had to remove all interface lines from that file. Then somehow mysteriously NM would ignore them in later versions so that it would work without entirely removing them. But as of late, something has changed and NM no longer works or would pick up the interface while there is still a reference in "/etc/network/interfaces". Don't ask me why, I simply think that's yet another bug... a very annoying one.

Thanx it worked for me , very nice help!

---

