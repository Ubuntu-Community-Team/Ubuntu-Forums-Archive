---
title: "[SOLVED] Network freezing"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by Zeratul021 on 2008-03-05
Hi, i have run into unknown network issue.
I have installed 7.10 on my laptop (amdx2turion, 1GB ram, ASUS) and my network connections experiences random blackouts lasting around 90secs. My friend has nearly similar notebook with same ubuntu installation but he hasnt it. I used to run on 7.04 and everything was fine until my my book was taken for repair and motherboard was changed with realtek network card as well. 
Any ideas or experience with this? thanx
And also friends computer can use nonfree drivers for his card to have some extra desktop effects enabled. If i turn them on, i experience random total freezes needing hard reboot. 

Thanks for all comments,

best regards

---

### Post by Zeratul021 on 2008-03-06
Problem seems to be fixed. 
Problem is closely described and solved here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141343](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141343)
It is due driver incompatibility in gutsy with RTL 8169 vs 8168b device.

---

