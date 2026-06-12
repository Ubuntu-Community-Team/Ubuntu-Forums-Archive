---
title: "wpasupplicant_0.5.7-0 actually has version 0.5.5 ?!"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by jadzy on 2007-07-24
Hi, 

I've got a version problem that is causing me some confusion.

When i run 'wpa_supplicant -v' it tells me the version installed is 0.5.5.  Only the package i've got installed is wpa_supplicant_0.5.7-0ubuntu2_i386.deb.

surely that should have version 0.5.7 in it?!

Tried reinstalling the package, no difference.

So... confused.  What gives?

S

---

### Post by spd106 on 2007-07-25
Going by the [changelog]("https://launchpad.net/ubuntu/feisty/+source/wpasupplicant/+changelog"), there were patches added to the version 0.5.5 so that in effect it has become equal to 0.5.7. I must confess that I'm not expert on the intricacies of package maintenance, so I can't say for sure. 

If you must have v0.5.7 then you could try to get a backport from Gutsy or perhaps build it from source. It does have many links to other files so it might not be so easy to just rip it out and replace.

Is there a specific feature or bug fix that you need?

---

