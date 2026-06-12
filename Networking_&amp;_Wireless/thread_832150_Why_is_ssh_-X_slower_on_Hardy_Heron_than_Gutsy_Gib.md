---
title: "Why is ssh -X slower on Hardy Heron than Gutsy Gibbon?"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by cbrinegar on 2008-06-17
I have machines running both recent Ubuntu releases (7.10 and 8.04), and when I ssh -X to the machines with Hardy Heron (8.04) GUI programs are not as responsive as I expect.  Below is a summary of the behavior:

Slow:
ssh -X from GG to HH
ssh -X from HH to HH
ssh -X from HH to itself

Fast:
ssh -X from GG to another GG
ssh -X from GG to itself
ssh -X from HH to GG

The behavior is that scrolling, typing, and mouse clicks are not very responsive.  Running the applications tested by sitting at the machines (not through ssh) results in normal operation.  The applications tested have been Matlab, gvim, and gedit, and I don't believe the problem is specific to any of those programs.

Of course, GG and HH run different versions of the sshd (4.6 vs 4.7), and I am wondering if that is the problem or if anyone else has encountered this behavior with Hardy Heron.

---

### Post by cbrinegar on 2008-06-18
The same behavior exists when connecting using telnet (temporarily installed for testing).  Also, internet speed tests show that both the GG and HH machines have very similar upload and download speeds, and all the machines are on a fast local network.  And no significant background processes are running.

---

