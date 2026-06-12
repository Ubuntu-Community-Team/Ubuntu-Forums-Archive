---
title: "Can't connect to Windows PC"
date: 2005-06-08
forum: Networking &amp; Wireless
---

### Post by KLineD on 2005-06-08
Hi all! I'm trying to setup a home network.

I get to the internet using ADSL. The connection is already shared with a 4 port router and all the PCs can get to the internet with no trouble.

My ISP assigns dynamic IP and the router assigns static IPs (192.168.2.x) to the other computers. I set up SAMBA and I can see the windows computer (192.168.2.198) from Ubuntu (192.168.2.199). My Windows computer can get into the ubuntu computer, list shared folders, read/write, all of it. 

The problem is my ubuntu computer, it sees the windows computer but it can't list folders, even ping fails. From the windows computer I can ping fine to ubuntu, but not the other way.

Any tips???

---

### Post by localzuk on 2005-06-08
[QUOTE=KLineD]Hi all! I'm trying to setup a home network.

I get to the internet using ADSL. The connection is already shared with a 4 port router and all the PCs can get to the internet with no trouble.

My ISP assigns dynamic IP and the router assigns static IPs (192.168.2.x) to the other computers. I set up SAMBA and I can see the windows computer (192.168.2.198) from Ubuntu (192.168.2.199). My Windows computer can get into the ubuntu computer, list shared folders, read/write, all of it. 

The problem is my ubuntu computer, it sees the windows computer but it can't list folders, even ping fails. From the windows computer I can ping fine to ubuntu, but not the other way.

Any tips???[/QUOTE]
 Check that you do not have a firewall enabled on the Windows box. Something like ZoneAlarm can be a royal PITA. Windows firewall might also be the problem - check that you have allowed network shares access via it.

---

### Post by KLineD on 2005-06-08
[QUOTE=localzuk]Check that you do not have a firewall enabled on the Windows box. Something like ZoneAlarm can be a royal PITA. Windows firewall might also be the problem - check that you have allowed network shares access via it.[/QUOTE]

Turns out that Windows Firewall was the problem. The windows computer ugraded to SP2 and it turned on the firewall.

Thanks a lot!

---

