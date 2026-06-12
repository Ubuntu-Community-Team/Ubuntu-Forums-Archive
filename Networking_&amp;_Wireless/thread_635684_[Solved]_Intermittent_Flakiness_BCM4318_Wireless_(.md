---
title: "[Solved] Intermittent Flakiness BCM4318 Wireless (laptop)"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by mverrilli on 2007-12-09
I have an HP dv4225nr laptop with a Broadcom BCM4318 built-in wireless adapter.  I just wanted to post in case anyone has the same issue.  I'm running on gutsy.

Issue: 

Intermittent flaky connection.  Sometimes it would work perfectly, then others the connection would have many dropped packets.  Restarting would  not always help.  I also noticed that I was getting a large number of RX packet errors (in ifconfig).  

The only way I could find to fix the problem was to install the windows drivers with ndiswrapper instead of the bc4xxx module. But it worked and it had a side effect of letting me connect at 54Mbs speed instead of 24.  

I just wanted to post because this issue is what was keeping me in Windows most of the time.  Now I can try qemu or vmware for the few Windows things I need and stay in Ubuntu! :)

---

