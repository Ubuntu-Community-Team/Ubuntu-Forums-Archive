---
title: "Bizarre resolver program after Feisty upgrade"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by Linux-Leach on 2007-05-06
After upgrading to Feisty from Edgy, I now have a rather bizarre resolver problem on my workstations.

The following are the results of "ping":

1.  Ping an external internet FQDN - OK
2.  Ping an internal hostname (without domainname) - OK
3.  Ping an internal complete FQDN - "unknown host"

This is using the iputils-ping.  The bind9-host works fine regardless.  There must be a difference in how these operate, and other apps must use whatever iputils-ping uses - because this extends to all the applications (firefox, konqueror, etc).

No changes were made to the rest of the network - just upgrading these two workstations to Feisty.  I have no idea what this means or how to fix it.

---

### Post by sancho666 on 2007-05-28
Hello,

I've had the same problem until I looked for it on google.
I found the answer:

[http://ubuntuforums.org/showthread.php?t=420183](http://ubuntuforums.org/showthread.php?t=420183)

---

### Post by Linux-Leach on 2007-05-28
That was indeed the problem.  My configuration happened to be exactly wrong for the avahi/mnds setup - I use a ".local" domain for our LAN.  I'd resolved it previously but didn't post an update here.  Went through and killed all the avahi stuff - no more problems.

Thanks for following up with me.

---

