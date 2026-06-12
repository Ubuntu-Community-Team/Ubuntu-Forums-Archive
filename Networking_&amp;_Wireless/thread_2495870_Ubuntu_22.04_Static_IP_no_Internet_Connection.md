---
title: "Ubuntu 22.04 Static IP no Internet Connection"
date: 2024-03-05
forum: Networking &amp; Wireless
---

### Post by thealphaweasel on 2024-03-05
Hi there
I have a VM of Ubuntu 22.04 running in TrueNAS Scale. I had it set with a static IP as I am running an SQL Server on it.
However now whenever I set a Static IP, I get no Internet Connection. If I use Automatic, I get internet but not on Static.
It's a default subnet at 255.255.255.0, I have checked for IP address conflicts and there are none. I have tried multiple different IP Addresses but nothing.
As soon as I set it to Automatic it works but since i'm running a SQL Server I want it Static.

Any help would be great
Thanks

---

### Post by TheFu on 2024-03-05
What do you mean by "get no Internet Connection?"   Can you ping 1.1.1.1?  Can you dig google.com?

---

