---
title: "NO DHCPOFFERS received - linksys WRT150N"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by peevee07 on 2008-01-08
I've read the other posts and share the frustration of those who can't connect. Here's my situation. I'm running 7.04 with a Motorola pcmia card. I had a d-link wifi router on the main box and everything worked fine until the router fried. I've replaced it with a Linksys WRT150N. Got it to work on the Dell running XP. And managed to get it to work on my IBM T-30 ubuntu laptop. But only for 30 seconds! Late at night, I was satisfied that the system was working and shut it down and went to bed. Since then I have not been able to connect. I get as far as NO DHCPOFFERS received. I have found other posts regarding command line connection and debugging very helpful, but not helpful enough to get me working. iwlist scanning tells me it can pick up the signal. I do the iwconfig with the correct parameters. I have tried ifdown and rm of the pid and ifup eth1. I've also tried networking restart. Anybody out there that can text me through this? Help needed big-time.

---

### Post by peevee07 on 2008-01-11
I've been working from the command line for some time. My frustration continued until I removed networkmanager. I hope this is a solution that lasts more than a day.

I also found that one posting suggested the prefix of s: before the WEP key when doing a iwconfig eth1 key .... command. That did not work for me. Rather I used iwconfig eth1 key "xxxxxxxx" with the quotation marks.

---

### Post by peevee07 on 2008-01-16
Alas, the solution I posted above did not last. I'm back to NO DHCPOFFERS received. Sigh.

---

