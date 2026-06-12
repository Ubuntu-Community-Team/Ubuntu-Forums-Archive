---
title: "Altering Ip address Renewals"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by Bicavis on 2007-04-02
I've a debian dhcp server running which has lease times set at rather small intervals.  No reason in particular they are set low, just defaulted and I haven't changed it yet.

Now the problem is that the client(Ubuntu) is constantly alternating between 2 ip addresses for renewal.  I could up the renewal times to large amounts but I'm more interested in why it is occurring.  

The strange bit is that this has never been an issue before.  Once it established an initial ip, it always requested the same one, but now it requests  one then the other.  It's not perfectly alternating  but seems to keep one for a 5-8 renewals then switches to the other.  

There are no other machines that are interfering with the renewals of this machine. 

Anyone know why the dhclient would alternate between two addresses when it used to just renew the same one.  (There is also a large pool of ip addresses available, no shortage)

(I know i can up the intervals and set static ips based on hw addresses, I'm just trying to understand why this occuring when it had not before)

Thanks in advance for any info on this

---

### Post by Floppyjoe on 2007-04-02
I have had a problem where my webserver needed to be rebooted and when i did this the router still had the lease in it and offered up a different IP for the webserver. I don't know if something similar might cause your problem.

---

