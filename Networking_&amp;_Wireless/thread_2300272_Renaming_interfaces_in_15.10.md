---
title: "Renaming interfaces in 15.10"
date: 2015-10-24
forum: Networking &amp; Wireless
---

### Post by kevin71 on 2015-10-24
Previously this was accomplished by editing 70-persistent-net.rules, however this file is not present on freshly-installed 15.10 server. Also none of the procedures for generating the file seem to work

What is the procedure for renaming interfaces now, so I can import my firewall config from my backup (they were named eth0, eth1, etc then, now its enp1s7, enp1s8, etc)

---

### Post by matt_symes on 2015-10-24
Hi

You can turn it off globally by booting with the kernel parameter

```
net.ifnames=0
```

Not tried to though as i'm still on 14.04.

From an email on the ubuntu devel mailing list. 

Kind regards

---

### Post by kevin71 on 2015-10-24
I had to manually create the 70-persistent-net.rules after adding the kernel parameter, but it seems to be working. Thanks!

---

### Post by Hadaka on 2015-10-24
Hi, it may revert back on the next cold restart,
did you read this,,[http://news.softpedia.com/news/Here-s-How-Persistent-Network-Interface-Names-Will-be-Implemented-in-Ubuntu-15-10-Ubuntu-16-10-and-Debian-9-483274.shtml](http://news.softpedia.com/news/Here-s-How-Persistent-Network-Interface-Names-Will-be-Implemented-in-Ubuntu-15-10-Ubuntu-16-10-and-Debian-9-483274.shtml)
it seems there are some unique changes,starting in 15.10,
/lib/udev/rules.d/75-persistent-net-generator.rules  is now
/lib/udev/rules.d/net.ifnames <- maybe??
the article in the above link mentioned a "tutorial/guide" on how to
rename with the new changes, beyond that,,,I dont have 15.10
so i was not able to test,
hope this helps

---

