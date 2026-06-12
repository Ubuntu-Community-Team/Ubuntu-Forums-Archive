---
title: "Internet connection suddely vanished"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by ralphmerridew on 2007-01-18
Setup:
Dual boot (linux / windows) -- router -- cable modem

Earlier today, my computer stopped being able to connect out while booted into linux.  (I can't even reach the router at 192.168.1.1.)  The same computer can connect out fine under Windows.  Any idea what's wrong?

---

### Post by Iowan on 2007-01-18
Will it ping the router?
Does it have an IP address (DHCP or static)?
What are the results of **ifconfig**?

---

### Post by ralphmerridew on 2007-01-18
> **Iowan said:**
> Will it ping the router?
Does it have an IP address (DHCP or static)?
What are the results of **ifconfig**?

Pinging the router gives an error along the lines of "Can't connect".  (I'm in Windows right now, and can't recall the exact message.)

It uses DHCP.

After boot, ifconfig only lists "lo".
If I manually "sudo /sbin/ifconfig eth0 up", it lists eth0, (though it doesn't list an IP address in output), but I still can't connect out.

Do you need the exact responses?

---

### Post by ralphmerridew on 2007-01-18
I manually ran "dhclient" and my connection started working again.  Any idea how it got killed / why it stopped running on boot?

---

