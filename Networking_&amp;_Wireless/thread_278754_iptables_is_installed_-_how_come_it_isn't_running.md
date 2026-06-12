---
title: "iptables is installed - how come it isn't running?"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by xp_newbie on 2006-10-16
the title says it all: I have verified that iptables is install and I have discovered that it is not running (for some reason).

How do I make it run?

Is it a service (that should be added using sysvconfig)?
Or is there some other mechanism to run iptables in Ubuntu?

Thanks!
Alex

---

### Post by woedend on 2006-10-17
iptables is but an empty shell..you can either write rules for it yourself, or, easier yet, install the package firestarter.
firestarter will show in sysvrcconf, or you can start it manually.

---

### Post by TheWizzard on 2006-10-17
see also: 
[http://ubuntuforums.org/showthread.php?p=1626560#post1626560](http://ubuntuforums.org/showthread.php?p=1626560#post1626560)

---

