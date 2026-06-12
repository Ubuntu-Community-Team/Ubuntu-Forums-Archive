---
title: "Can't change DNS servers"
date: 2016-11-20
forum: Networking &amp; Wireless
---

### Post by k0tt0n on 2016-11-20
I'm wanting to change my DNS server and have done so in the past but for some reason I cannot now. This is what I'm doing, I open network manager, choose my connection, then edit connections, go to IPv4 settings. here by default the Method is set to Automatic (DHCP). So I change that to Automatic (DHCP) addresses only. Now here's when the problem arises. As soon as I put a number into the DNS servers box, the 'SAVE' tab at the bottom blanks out. So basically I'm following the same procedure as I always have, except it's now not possible to save anythingI edit.

any advice appreciated.

thanks

---

### Post by jeremy31 on 2016-11-20
See if it works if you leave it at Automatic (DHCP) and add the DNS

---

### Post by bearlake on 2016-11-20
Is this 16.10? If so there's a bug.

If 16.10 or 17.04 read post 3 & 5, it works.

[https://ubuntuforums.org/showthread.php?t=2340042&p=13557382#post13557382](https://ubuntuforums.org/showthread.php?t=2340042&p=13557382#post13557382)

---

### Post by chili555 on 2016-11-20
> As soon as I put a number into the DNS servers box, the 'SAVE' tab at the bottom blanks out. Does it blank out if you put in a single number; 8, for example? If so, that's expected and correct, as "8" isn't a valid IP address nor a valid DNS nameserver.

If you continue and put in, for example, 8.8.8.8, 8.8.4.4 does Save remain blanked out?

---

### Post by chili555 on 2016-11-20
> **bearlake said:**
> Is this 16.10? If so there's a bug.

If 16.10 or 17.04 read post 3 & 5, it works.Post #3 and 5 where? Did you miss a link?

---

### Post by bearlake on 2016-11-20
> **chili555 said:**
> Post #3 and 5 where? Did you miss a link?

Sorry, My bad and now fixed.

---

