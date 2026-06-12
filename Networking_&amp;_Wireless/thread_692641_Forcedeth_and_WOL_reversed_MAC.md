---
title: "Forcedeth and WOL reversed MAC"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by fain on 2008-02-10
Hello I am trying to get a on board NIC to wake on lan. When i initially boot up the mac address is correct. When i go into suspend the first time, the magic packet works good. The second time i suspend, the magic packet doesn't work so well. It seems the MAC address reverses every suspend but the magic packet doesn't work after the first suspend no matter what mac i use :(

example macs

initialboot
AB:BC:EE:EF:01:02    eth0
after first suspend
02:01:EF:EE:BC:AB    eth2
second suspend
AB:BC:EE:EF:01:02    eth0

and so on...

Ive read that this is a kernel issue.
Any one know of a fix?

I found this patch but i wouldn't really know where to start on installing it. Or even if it will fix it.

[http://www.mail-archive.com/linux-kernel@vger.kernel.org/msg246996.html]("http://www.mail-archive.com/linux-kernel@vger.kernel.org/msg246996.html")

---

