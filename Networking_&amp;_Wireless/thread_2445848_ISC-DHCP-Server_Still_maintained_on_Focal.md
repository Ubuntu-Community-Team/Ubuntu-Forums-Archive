---
title: "ISC-DHCP-Server Still maintained on Focal ?"
date: 2020-06-20
forum: Networking &amp; Wireless
---

### Post by Andrew_Welham on 2020-06-20
Quick general question,
There is a lot of bug reports for isc-dhcp-server for focal (including one where it crashes on launch if in a cluster), but not much activity. Does any one know is this package is still maintained (or how i can find out).
Many Thanks

---

### Post by SeijiSensei on 2020-06-20
[https://launchpad.net/ubuntu/+source/isc-dhcp](https://launchpad.net/ubuntu/+source/isc-dhcp)

There's a build for Groovy Gorilla (20.10) so I presume it's being maintained.

The current bug list:

[https://bugs.launchpad.net/ubuntu/+source/isc-dhcp](https://bugs.launchpad.net/ubuntu/+source/isc-dhcp)

---

### Post by Andrew_Welham on 2020-06-21
I know the bug list is there , but it does not look to have been looked at for months even before focal was released, and isc-dhcp server crashes when launched in clustered mode on focal, so its completely useless. Multiple users have this issue, but this amongst other bugs are not being reviewed as far as i can tell. I've downgraded to the 18.04 version because of this. Just wondering if i should avoid isc-dhcp sever all together.

---

