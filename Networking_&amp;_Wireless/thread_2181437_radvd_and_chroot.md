---
title: "radvd and chroot"
date: 2013-10-17
forum: Networking &amp; Wireless
---

### Post by casey5 on 2013-10-17
Hello,
 I was wondering if anyone has gotten radvd to work in a chroot enviroment. 

I can get radvd to work by itself
I can get radvd to work with dropping privilleges (-u radvd)
but I can't get it to work by having it chroot into its own enviroment.  (-u radvd -t /srv/radvd)
   I keep getting an error stating that the config file has its permissions incorrect, which when I add the -d 5 to the command, it tells me no such user radvd, which isn't true because it worked the step before.  so I have to be missing something in the enivorment which I don't have a clue as to what it is. I've tried putting the passwd, group, and shadow files there, no go. 

Any thoughts?
Casey

---

