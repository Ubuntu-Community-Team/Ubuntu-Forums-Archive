---
title: "help networking with winxp."
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by evilc on 2006-11-19
I have a friend who has 6 computers networked in Winxp and wants to network his Ubuntu laptop  to the rest.  He has  installed samba  and  a suggested  smb.conf file , we now can see and use the other computers and use the internet, but they (winxp) computers can't see the Ubuntu laptop. Just to make it more complicated they now can't see each other while laptop in network connected, that I think is because the iP is set to 192.168.1.1 ( via the smb.conf which is itself). His internet IP is not static.

I have had a look at Samba site and it seems to refer to "servers" all he has got is 6 computers and a broadband modem connected to a router box.

As I am only just learning Linux myself (and he knows nothing at all) I need some simple instructions how to get him up and running, any help would be much appreciated.


TIA

---

### Post by FrodoB on 2006-11-19
Maybe if you could publish the smb.conf file someone could pipe in?

Also, get the output of:

$ sudo iptables -L

Just to make sure that the firewall is not involved at all.

---

