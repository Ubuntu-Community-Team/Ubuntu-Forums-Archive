---
title: "Anyone know how I set up virtualization/virtualbox to play with networking?"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by triptoe on 2007-09-07
For instance... I want to use my host system as a server... and my guest operating system as a client... or vice versa it doesn't matter... but I heard that i am suppose to be able to do this somehow.

I went and tried to ping my host from my currently installed client OS and it timed out... i tried to ping my guest from my host and it also timed out... how do i get it working?

My IP address from my router is assigned to 192.168.1.103 for my host computer. My client (windows xp) for some reason is given 10.0.2.15

---

### Post by thelinuxguy on 2007-09-07
> **triptoe said:**
> I went and tried to ping my host from my currently installed client OS and it timed out... i tried to ping my guest from my host and it also timed out... how do i get it working?

My IP address from my router is assigned to 192.168.1.103 for my host computer. My client (windows xp) for some reason is given 10.0.2.15

Try changing the IP address assigned to your XP box. Something like 192.168.1.X.

Also have you configured Virtualbox networking in bridge mode? Otherwise you will be able to access the host from the guest but not the reverse since the default network configuration is NAT.

Have a look at this post by me in some other thread: [http://ubuntuforums.org/showpost.php?p=2723644&postcount=15](http://ubuntuforums.org/showpost.php?p=2723644&postcount=15)

---

