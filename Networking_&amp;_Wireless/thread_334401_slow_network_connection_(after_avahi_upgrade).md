---
title: "slow network connection (after avahi upgrade)"
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by dimkal on 2007-01-08
Hello, couple of days ago avahi packages were updated on my edgy (AMD64).  Since that moment I start having network problems... One problem is that every ssh connections (regardless of the server) are dropping after few minutes of being connected with the following message:

```
Read from remote host faradis: Connection reset by peer
Connection to faradis closed.
```

another problem that each firefox request has become much slower.

our system administrator suggested to disable IPv6, which I did, but still the connection is slow and ssh connections are still dropping.

another point worth mentioning is that when I run "sudo /etc/init.d/networking restart" this solves the slow connection for few minutes but then the problem reoccurs.

like i said, this problem started happening as soon as I upgraded the avahi packages suggested by ubuntu.   I tried to grep for avahi packages but they don't seem to be running. also i've tried "sudo /etc/init.d/avahi-daemon restart" but this command apparently does not do anything (usually these things say... stopping [OK]; starting [OK]) for for avahi-daemon no message is echoed. 

i also get these messages when i run 'dmesg', but i don't know if they are connected to this problem...
```
[17692.221970] warning: many lost ticks.
[17692.221972] Your time source seems to be instable or some driver is hogging interupts
[17692.221982] rip __do_softirq+0x54/0xe0 
```

where do i start troubleshooting this?

---

