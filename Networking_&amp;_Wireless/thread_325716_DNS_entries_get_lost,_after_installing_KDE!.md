---
title: "DNS entries get lost, after installing KDE!"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by DoktorNo on 2006-12-26
UpHi there,

I have a home network, with DSL modem, directly connected to eth0. All IP's are static, there is no DHCP and other stuff. 

Some time ago, I tried the KDE desktop enviroment, installed via aptitude. It didn't suited me best, so I removed it again with aptitude, so there is no unresolved dependencies and other orphaned packages.

But since this stunt, every time I reboot my box, the DNS servers are erased. The network works fine, if I manually set the DNS IP's in network-config. It is really annoying!! ](*,) 

Plese, help me!

Update: I am trying to reconfigure the resolvconf packadge.

Update #2: I have disabled the dynamic updatets of resovf.conf. No change. :(

Update #3: 
```
sudo apt-get remove resolvconf
```
And then everything is OK. :| Luckly I doesn't need DHCP resolving&#8230; :-?

---

