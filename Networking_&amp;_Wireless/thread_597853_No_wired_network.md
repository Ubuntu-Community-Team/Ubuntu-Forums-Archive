---
title: "No wired network"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by kob0724 on 2007-10-30
My wired networking is not working. I have it set for DHCP and when I look at my connection properties I see that is has been assigned and IP address, has a default route, has DNS servers etc. But if I try to even ping my default route in the terminal I get "destination network is unreachable." Needless to say firefox doesn't work. Can't ping google either. Any ideas?

---

### Post by KCPokes on 2007-10-30
Verify whether the IP address assigned is actually within your allotted range.  When things go flaky it tends to assign an ip address that is invalid (169.XXX.XXX.XXX) in your range (192.168.1.XXX).  This gives you the impression that you have an IP address when its not in fact valid.  Does this happen each time you boot?

---

### Post by kob0724 on 2007-10-30
The ip address is a valid one. It of the same format that I get when I use my Windows partition. Yes, this happens every time I reboot. It was working the other day, but only after a few disconnects and reconnects.

---

### Post by kob0724 on 2007-10-31
Not sure if this is relevant. But i was looking at the interface statistics and i noticed that the interface was _constantly_ recieving a small amount of data. Like mabye 1.5 kb/s.

---

### Post by kob0724 on 2007-11-01
Bump

---

