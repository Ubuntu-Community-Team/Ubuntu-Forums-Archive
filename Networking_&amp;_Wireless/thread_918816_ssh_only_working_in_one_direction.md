---
title: "ssh only working in one direction"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by Amblikai on 2008-09-13
Hi everyone, been lurking on these forums for a while, this is the first time i haven't found an answer which hasn't already been said.

My problem is that i have two computers, networked through a router.

Both have internet access and i can ping computer 1 from computer 2 and vice versa.

However, i can ssh from computer1 to computer2 but not the other way round.
I'm new to ssh and networking in general, i've been using linux exclusively for around 5 years, and currently on kubuntu.

I hope its something simple. Thank you for your time.

Kai.

---

### Post by Amblikai on 2008-09-13
Oops, well it was something simple! i had to install openssh-server on one of the machines.

I've come up with another problem now though. One of the machines is called Optimus-prime ans export DISPLAY=$Optimus-prime:0.0 doesn't seem to like the '-'. Should i change the name of the computer or is there a way round it?

Thanks.

---

