---
title: "Synology Nas ping Ubuntu Latop 20.04.1 high delay problem"
date: 2022-12-05
forum: Networking &amp; Wireless
---

### Post by haso2007 on 2022-12-05
In LAN, when Ubuntu ping Nas, the  delay is only 2ms, but reverse Nas ping Ubuntu delay is much more about 100ms, What's the problem?
I'm new for the Linux,look forward to your help to solve the problem should be in the Ubuntu setting. 

But intresting, When I do the ping on both side in parallel, then the 100ms change to about 20ms. Now I use this way to temporary SSH connection, otherwise the SSH is delay too much sometime 2-3 second on the client,Crazy.

---

### Post by TheFu on 2022-12-06
Slow networking that isn't related to the wrong driver or bad hardware/cables, it often incorrect DNS. Check all the DNS first on all systems.
If you aren't running a local DNS that contains the lookup for the Ubuntu system, then DNS isn't being used and the only real options are
a) edit the /etc/hosts on the NAS box
b) setup a LAN DNS so all systems on the LAN use it first, before asking internet DNS for answers.  A PiHole is a useful tool for this and ad-blocking.

---

