---
title: "Multiple MACs on one NICs"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by jsatubnutufroums on 2008-03-26
Hi,
I would like to use multiple virtual interfaces with different MAC addresses on a single network adapter. 
At first, I find the ['MultiMac]("http://www.primianotucci.com/default.php?view=57")'.It is invalid and  has a bug "All tap devices have the same MAC address for outside world". So 'MultiMac' isn't a solution.
At second, I install VMWare, create a virtual machine with bridged networking, and install Ubuntu Linux. I find that Guest OS has different MAC address from Host OS. Its outgoing request still has different MAC address.
But I want to simulate 100 PC and I don't think the VMWare is appropriate to me. 
So is there any solution I can try? Thank you.

---

