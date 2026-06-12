---
title: "Block internet"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by 2LSS on 2009-07-30
I'm looking for a way to block internet access to a specific windows program running under wine in 8.04. I tried to find the port with netstat but I have no clue how to interpret the data. I also tried to install tuxguardian with no luck. I've read that I can block ports with iptables but after reading the man page I am still lost. What would be the best way to do this?

---

### Post by nhasian on 2009-07-30
you can use the ubuntu firewall:

[http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)

---

### Post by XCan on 2009-07-30
> **nhasian said:**
> you can use the ubuntu firewall:

[http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)

Actually you can't. UFW doesn't support rules for outgoing traffic. You can either add it to iptables manually, but I think simply setting it up with Firestarter (in repos) would be easier.

---

