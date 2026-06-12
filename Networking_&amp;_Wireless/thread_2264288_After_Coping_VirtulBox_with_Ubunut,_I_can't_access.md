---
title: "After Coping VirtulBox with Ubunut, I can't access Internet"
date: 2015-02-06
forum: Networking &amp; Wireless
---

### Post by dejan.b on 2015-02-06
I spent 2 days setting up Ubuntu Server 14.04.1 as guest inside VirutalBox 4.3.20 on my Windows 7 laptop Host and it works super fine.

Then I copied the Virtual Box to my office PC and there I can't make Ubuntu get access to the Internet, but I can ping Ubuntu so the network works only one way, towards Ubuntu?!

I used bridged network - the same setup on both computers, and I even tried with Advanced network settings to select
Adapter Type as Intel PRO/1000 MT Desktop and Promiscuous Mode to Allow VMs and NOTHING!

I even disabled the firewall and still no luck.

The weird thing is that my host can ping guest and access it's Apache/MySQL services but the guest has no access to anything, it can't ping any address out of the box... like it does not have the route but netstat -rn show that it's GW is OK.

I've seen older posts from the time Ubuntu used net-persistent rules but I think that does not apply any more since that rule is not in /etc/udev/rules.d any more

Can anybody help, please?

---

### Post by SeijiSensei on 2015-02-06
Why do you need to use bridging?  Having the virtual machine use NAT is much more portable.

---

### Post by dejan.b on 2015-02-09
The idea is to let my coworkers can access to testing platform. With NAT it does not work.

---

