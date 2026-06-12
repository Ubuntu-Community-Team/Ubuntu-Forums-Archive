---
title: "Xubuntu: Mostly internet failure"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by LanceHaverkamp on 2006-10-27
Using Xubuntu, both 6.10 & 6.0 I cannot connect to any web sites nor my own router with Firefox or gaim.  However with both 6.0 & 6.10, I can **ping** everywhere!  Google, my ISP's DNS...

Any idea why I can ping the net, but can't surf?

I'm using the liveCD versions of Xubuntu on an Athlon XP box that normally runs MEPIS/ubuntu Linux with no internet problems at all.  I've tried both static & dynamic IP; both direct connect & auto-detect in firefox.  On a wired, ethernet, DSL LAN.

I have no idea what the problem could be!  Any ideas?

Thanks,

Lance

---

### Post by john_spiral on 2006-10-28
is your router using DHCP (gives connecting computers an ip address)?

might need to set that in the network settings under xubuntu.

johne

---

### Post by stream303 on 2006-11-13
Hmm... doublecheck your /etc/resolv.conf and see if you might be having dns issues like the loss of your isp's dns nameservers..

---

