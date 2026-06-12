---
title: "No network connectivity after reboot"
date: 2005-07-17
forum: Networking &amp; Wireless
---

### Post by Heretic09 on 2005-07-17
I've been messing with ubuntu for a couple of months and networking, samba as well as internet, has been fine. However last night after rebooting it simply won't connect to the internet or to any of my windows machines. I've tried rebooting again but still the same problem. I haven't made any major changes such as installing new firewall software or upgrading the kernel.
 
doing sudo ifdown eth0 && ifup eth0 gives me:

sit 0: unknown hardware address type 776
sit 0: unknown hardware address type 776

Listening on LPF/eth0/00:07:e9:7b:85:78
Sending on LPF/eth0/00:07:e9:7b:85:78
Sending on socket/fallback

DHCPRELEASE on eth to 192.168.2.1 port 67
send packet: operation not permitted

ifup: failed to open statefile etc/network/ifstate: permission denied

If I connect directly to my cable modem it hangs on startup where it says "configuring network interface"

Anyone have any ideas on what is perventing my system from connecting to any network, local or otherwise?

---

### Post by Heretic09 on 2005-07-18
When I ping my own ip address I get operation not permitted error, even if I try to ping 127.0.0.1.

---

### Post by Heretic09 on 2005-07-18
Nevermind, fixed it.

---

### Post by Rogue Elephant on 2005-07-20
[QUOTE=Heretic09]Nevermind, fixed it.[/QUOTE]
 how?

---

