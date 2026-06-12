---
title: "How to remove nas0 in ATM bridging (br2684ctl)"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by geppetto on 2008-01-25
I have a minor problem with the br2684ctl utility, and I have already spent some time looking for an
appropriate mailing list.

It's OK to set up a connection: no problems on that side. But, when I
want to switch the connection down, and up again (for instance,
suspending the PC), the remainings of the previous connection block the
way: I am unable to remove completely the nas0 interface. A "ifconfig
nas0 down" is not sufficient (some dev files persist),
and the successive invocation of br2684ctl fails (**nas0 already existing**).

Any help? An appropriate howto would be OK, otherwise I'll be happy to write one when I know the solution.

Thanks!

---

### Post by wolfie2x on 2008-07-04
I have the same problem.. only a restart works for me.. any help please?

---

