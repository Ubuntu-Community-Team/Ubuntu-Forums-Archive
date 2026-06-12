---
title: "Bridge connections"
date: 2006-12-27
forum: Networking &amp; Wireless
---

### Post by tgeof on 2006-12-27
Hi, I've got a laptop running 6.10 with a wireless card (eth1) and a wired port (eth0).  I have a desktop running 6.10 with wired port (eth1).  I want to connect from the desktop(eth1)---laptop(eth0)-----laptop(eth1)-----wireless router.

is there any way to do this?  thanks.

---

### Post by dbott67 on 2006-12-27
You can use iptables to make the laptop into a NAT router:
[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)

You can also install Firestarter from the repos (which is just a front-end for iptables) that will allow you to masquerade/NAT).

-Dave

---

