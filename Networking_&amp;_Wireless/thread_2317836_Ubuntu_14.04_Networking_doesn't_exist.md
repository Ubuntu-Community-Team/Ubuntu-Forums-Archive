---
title: "Ubuntu 14.04 Networking doesn't exist"
date: 2016-03-20
forum: Networking &amp; Wireless
---

### Post by dyslabs on 2016-03-20
"Networking doesn't exist" is the best way I could put this problem.

My wired Ethernet connection isn't being detected by Ubuntu. I've done research, but no one else's problem is like mine.

So just some commands you'll probably want (I don't have Internet access on the machine, so its kinda a pain to type them out, but I will if it helps)
**sudo ifconfig -a**
only returns loopback

**lspci**
Nothing related to ethernet is returned

[B]sudo ifup eth0
[/B]Ignoring unknown interface eth0=eth0

Now, the most interesting to me **lshw -C network**
Returns nothing



I've been stuck on this all night and morning, any help is greatly appreciated. Thanks!

---

### Post by oldos2er on 2016-03-20
Moved to Networking.

So ```
lspci | grep Ethernet
``` returns nothing? What make/model ethernet device does the system have?

---

### Post by dyslabs on 2016-03-20
> **oldos2er said:**
> Moved to Networking.

So ```
lspci | grep Ethernet
``` returns nothing? What make/model ethernet device does the system have?

Right. I'm afraid I'm not quite sure, but I believe its a 3Com 905B.

---

### Post by dyslabs on 2016-03-20
Also, it was working fine yesterday, then I unplugged the cable and moved the computer and then plugged it back in and it hasn't been working since. I know I had the drivers installed.

---

