---
title: "wireless  and ethernet connectivity"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by robs2015 on 2011-01-15
I am using Ubuntu 10.10 desktop. I have successfully connected the desktop to a wireless network (eth0) and can ping remote hosts on that network.
When I connected, from the desktop, an ethernet cable to a local LAN (eth1) remote hosts on the wireless network become 'destination host unreachable' when I ping them.
Disconnecting the ethernet cable again allows me to ping remote hosts on the wireless network.
I have checked all IP addresses and they are correct. Both network work but no concurrently.
Why is this ?
 
Rob

---

### Post by cariboo on 2011-01-16
What you are experiencing is by design, you can use both, if you remove network-manager, and set up the connections manually.

---

