---
title: "Ubuntu Server Networking Question"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by Smartmonkey on 2008-08-25
I am setting up nagios box to monitor a few servers and am running into a problem with 1 host. Im not sure if its the newer build of ubuntu, as this was working on a box that had an hd failure.

Nagios is working great, I just cannot ping a .254 address:

ping x.x.1.254
Do you want to ping broadcast? Then -b


Anyone know why I cannot ping .254 any longer? is it reserved for broadcast in the latest version of ubuntu server (8.04)?

Thanks.

---

### Post by ilrudie on 2008-08-25
Usually X.X.X.255 is reserved for broadcast.  To see what your broadcast is actually set to you can always use ipconfig -a and look at the Bcast field.

---

### Post by Smartmonkey on 2008-08-25
Doh..

serious typo.. accidentally assigned that as my broadcast address on that box. It was 2 AM, i'll chalk it up to that.

thanks for your help.

---

### Post by Iowan on 2008-08-27
Mark this one [SOLVED] (under Thread Tools pulldown) so I'll quit checking it. ;)

---

