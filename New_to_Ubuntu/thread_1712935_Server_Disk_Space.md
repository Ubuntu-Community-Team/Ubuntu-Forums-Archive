---
title: "Server Disk Space"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by efision on 2011-03-23
I have just installed 10.04 server on 2 HP servers. One has raid 1 controlled by the HP 410i raid controller the other has raid 5 also theough the 410i.

The first system looks fine webmin reports 64.47 GB disk capacity and 17.94GB used. This includes a 6GB database and a backup of 3.5GB.

The second server has simply been installed as a LAMP server with no data installed at all and webmin says the disk capacity is 538.84Gb with 28.72GB used.

If I run df -h on this server the filesystem reports:

/dev/cciss/c0d0p1 539G Size, 1.4G Used, 511G Avail

Can anyone explain why I get this discrepancy?

---

### Post by aaaaalex on 2011-03-23
Must be a feature of webmin :-D

---

### Post by _0R10N on 2011-03-23
> **aaaaalex said:**
> Must be a feature of webmin :-D

Well, I'd agree. Don't pay attention to what webmin says, then.

---

### Post by aaaaalex on 2011-03-23
[http://www.webmin.com/community.html](http://www.webmin.com/community.html)

You could have a look there... Maybe post your findings again there. It could help the Webmin ppl to make their project even better.

---

### Post by tgalati4 on 2011-03-23
It's possible that the system (root) reserves 5% of memory that is used for housekeeping and also when disk space gets low to keep the machine running.  The 28GB used seems about right for that amount.

The df utility may not be aware of that hold on that disk space because it is a low-level utility, and until the space is actually used, it won't report it.

You can tune how much disk space root reserves through a kernel tuning parameter, but you will have to look it up.

So for those that like the new math:

5% of 539 GB is 26.95 GB + 1.4 GB for your minimal LAMP install = 28.35 GB.  Which is pretty close to the reported 28.72 GB used.

Do I get a lollipop?

---

### Post by aaaaalex on 2011-03-26
Spot on :-D

---

