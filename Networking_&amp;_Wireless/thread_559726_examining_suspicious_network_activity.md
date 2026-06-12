---
title: "examining suspicious network activity"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by pytheas22 on 2007-09-25
Hi all,

My USB dongle wireless card has two lights, one to indicate a connection and the other to indicate traffic.  Lately, I've noticed that the data-light has been steadily flashing (about one flash per second).  Until a week ago, it never did that, and I haven't made any changes to my network.  I rebooted and killed everything that I could think of that might be trying to access the Internet (gaim, Evolution, torrent clients...) and yet the light keeps flashing, indicating that there's data being transferred.

I am worried that something is trying to contact my computer that shouldn't be.  Is this a valid concern?  I used Firestarter but it shows no traffic from suspicious IP's.  Is there some other way to specifically check out what's in these packets that are coming in or going out every second?

---

### Post by Paulo79 on 2007-09-25
I noticed the same thing here (network activity every 1sec or so). I closed all apps, logged out, restarted, and I can still see this network traffic pattern in Gnome System Monitor. I'm not 100% sure, but I suspect it started this morning after I updated the kernel using Ubuntu's update facilities (kernel version Ubuntu 2.6.20-16.32-generic ).

**UPDATE**: I'm reporting this on a HP dv9000t laptop, Intel PRO/1000 wired Ethernet connection. Switching to wireless (Intel ipw3945 driver) makes the aforementioned network activity pattern disappear. Now I just switched back to the wired connection and the network activity started again every 1sec or so. This wasn't happening yesterday.

---

### Post by KCPokes on 2007-09-25
Even if your firewall was killing the packets as they reached your machine, it is still traffic.  Your firewall is software, thus the data still needs to reach your machine to be blocked.   If your machine is sitting within a private network (only your machines) then it could be as simple as something performing a broadcast; if you are sitting on the internet, the possibilities are endless as to where the traffic is coming.

---

