---
title: "Internet Dropping on Xubuntu"
date: 2014-08-21
forum: Networking &amp; Wireless
---

### Post by jacob46 on 2014-08-21
Hey guys,

So just today I've started having an issue where my connection is dropping every so often.  As frequent as every 1 minute, and as infrequent as every 20 minutes.

It's a wired connection.  I have virtualbox on my machine, but am not running it currently.

Any ideas?

thanks

---

### Post by varunendra on 2014-08-25
Sounds like a bad cable/contact. Have you tried another tested cable? Does this one work on other system/OS?

Please post the outputs of -
```
ifconfig -a
lshw -C network
```
..when it is dropped.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

