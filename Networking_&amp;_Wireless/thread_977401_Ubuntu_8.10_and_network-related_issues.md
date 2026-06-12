---
title: "Ubuntu 8.10 and network-related issues"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by mbeccaria on 2008-11-10
Just upgraded from 8.04 to 8.10 on a laptop dell precision M4300
Some issues already observed, here some main topics concerning network which I would like to signal:

1) boot is now extremely low. Pressing CTRL+F1 I can see the majority of boot time is spent in "Configure network interfaces". Can somebody explain/hint how to speed up this ?

2) I was previously using KVPNC to connected to my company intranet from home via openvpn. The last official release was 0.9.0. It was perfectly working on 8.04. It has stopped working on 8.10, claiming some problem with the activation of external programs. Found a post suggesting to upgrade to KVPNC 0.9.1 (not official yet), I have tried but it does not work. Then I have installed network-manager-openvpn package, configured the VPN but I cannot connect to my company's LAN. Any hint ? How can I verify the VPN has been established successfully ?
Is there any alternative VPN client tool I could use ?

3) when connected to LAN via the wired connection, there's no network icon on the upper right side of the desktop (where you typically have the power management icon, the volume, etc...) Is it normal ??

Thanks in advance for any reply to this post

---

### Post by mbeccaria on 2008-11-11
as an update on the above post, I have partially solved the issue of the openvpn. There's only one pending problem: when the VPN is on, I can reach the company's intranet, but I'm not able anymore to go to Internet.
Seems to be a DNS resolv.conf issue, but I still cannot sort it out.

---

### Post by superprash2003 on 2008-11-11
try this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

