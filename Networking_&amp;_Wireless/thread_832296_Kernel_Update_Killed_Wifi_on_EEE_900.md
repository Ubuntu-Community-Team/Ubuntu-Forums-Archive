---
title: "Kernel Update Killed Wifi on EEE 900"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by Bishop Hill on 2008-06-17
I'm running EEE Xubuntu on a EEE 900, and after a kernel update a couple of days ago the wireless does'nt work anymore. I've had this problem before, but then the procedures on help.ubuntu.com/community/eeepc/fixes helped me fix the problem. This time, however, it did not work. I've tried everything that I know (which is basiclly that on help.ubuntu.com/community/eeepc/fixes) , and nothing works.

Can someone help me, pretty please?

---

### Post by gmendoza on 2008-06-17
> **Bishop Hill said:**
> I'm running EEE Xubuntu on a EEE 900, and after a kernel update a couple of days ago the wireless does'nt work anymore. I've had this problem before, but then the procedures on help.ubuntu.com/community/eeepc/fixes helped me fix the problem. This time, however, it did not work. I've tried everything that I know (which is basiclly that on help.ubuntu.com/community/eeepc/fixes) , and nothing works.

Can someone help me, pretty please?

For starters, can you tell us which driver you are using?  Madwifi or Ndiswrapper?

---

### Post by Bishop Hill on 2008-06-17
> **gmendoza said:**
> For starters, can you tell us which driver you are using?  Madwifi or Ndiswrapper?

Ndiswrapper.

---

### Post by steeven on 2008-06-21
I found that aireplay-ng -9 (--test) will stop later injection. any following injection such -3 will failed!

don't use -9 for ipwraw driver!!!

---

