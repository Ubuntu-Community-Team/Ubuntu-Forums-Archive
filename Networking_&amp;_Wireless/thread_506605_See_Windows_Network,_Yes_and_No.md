---
title: "See Windows Network, Yes and No"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by spiderman1369 on 2007-07-21
I have 3 computers on a local network. Two Ubuntu Feisty and One Windows XP Pro.

I've never installed Samba on either Ubuntu Computer.

One Ubuntu box can see the Windows Network, the Windows Computer, and shares on the Windows computer.
The other Ubuntu box doesn't see **anything** at all when I go to Places -> Network.

Why is that?

Also, is there a way to reset all network settings to the default (i.e. Just like after a fresh install) in Ubuntu?
How about all settings, not just network???

Thanks for any help!

---

### Post by zanglang on 2007-07-22
Does the other Ubuntu box have a firewall installed (eg Firestarter)? You will have to open the ports used by Samba (137-139 and 445) so the NetBIOS requests get through.

---

### Post by spiderman1369 on 2007-07-22
No firewall...

running the command "iptables -L" on either Ubuntu computer gives the following...

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

