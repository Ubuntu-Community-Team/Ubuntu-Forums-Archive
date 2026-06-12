---
title: "netsed is broken: Segmentation fault"
date: 2016-09-17
forum: Networking &amp; Wireless
---

### Post by blauhirn on 2016-09-17
Hey!

I am redirecting packets via iptable to netsed.
*Netsed, however, is broken in xfce* as of Sept/2016, it seems: [This bug exactly]("https://bugs.kali.org/view.php?id=3551") happens to me, too (XUbuntu).

Now, I found a more recent netsed version, updated 2013 by some user & opensource, from [http://silicone.homelinux.org/release/netsed/](http://silicone.homelinux.org/release/netsed/). The error persists there.
(Details about the source code: I found the error happens in line 422 and 451. I tried setting r->fs and r->ts to 0 at the beginning at the function, but this causes weird behaviour upon forwarding (length is 108 bytes, but buffer contains only one letter etc.).)

I can't really figure out what is going on there and how  to solve it.

**Is anyone of you more familiar with C**, or has an idea how to fix it, or are there any alternatives to netsed out there, or should I ask this question somewhere else?

Thanks everybody.

---

### Post by mrsaros on 2016-10-09
patch for 
[LIST]
[*][[netsed_1.2.orig.tar.gz]]("http://archive.ubuntu.com/ubuntu/pool/universe/n/netsed/netsed_1.2.orig.tar.gz")
[/LIST]

```

232c232
< int rules;
---
> int rules = 0;
513a514,515
>       rule[rules].fs = 0;
>       rule[rules].ts = 0;



```

---

### Post by blauhirn on 2016-10-20
Nice!!! I applied these changes and the error is actually gone! You made the world a better place.

I can't really say if this version actually works fine though. Can you help me out one more time?
Running iptables with netsed together, the netsed output literally explodes.

[+] Got incoming connection from 192.168.0.102,57720 to SERVER_IP,57578
[*] Forwarding connection to SERVER_IP,57578
[+] Caught client -> server packet.
[*] Forwarding untouched packet of size 136.
[+] Got incoming connection from 192.168.0.102,57722 to SERVER_IP,57578
[*] Forwarding connection to SERVER_IP,57578
[+] Caught client -> server packet.
[*] Forwarding untouched packet of size 136.

(many a 100 times) (note how outgoing port increases by 2 with every "try")
and 

[+] Caught client -> server packet.
[*] Forwarding untouched packet of size 136.

(7 times)

I looked into Wireshark: not a single packet is being sent to my SERVER_IP!  Forwarding seems to be broken. netsed all eats them up. Does anybody have an idea why that could be the case? :confused:

Thanks.

---

