---
title: "FireFox can not see the Internet - Help"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by GMP on 2008-01-25
As most of the postings start, I am an Ubuntu newbie.

I am a Unix geek from years back, but have been carried kicking and screaming through Windows.  I decided to get back into Unix.

I am Network savvy, but I can not seem to get FireFox to connect to the Web.

I am ethernet connected.

I don't quite understand the "Allow Roaming" in the Network Config GUI, or the tick on the interface listing on the GUI.  However command line ifconfig reports that eth0 has an IP address that is in my DHCP range.  I can ping the router, and I can ping a real world URL and receive a reply (ping [www.google.com](www.google.com) is all good).  This proves both DNS and routing to be working.

I can ping from the Network Tools GUI as well.

However, when I start FireFox, and look for a real world URL ([www.google.com](www.google.com) again), FireFox reports "waiting for www.google.com".  If I wait long enough, a default page appears telling me that the web page took too long to respond.

My modem is configured as a NAT router.  The routing is working, as the ping works.  The same hardware booted to windows (with the same DHCP address) works fine.

I can only find a Proxy Config setting in FireFox,and as I am effectively directly connected to the Internet (Via NAT), I have set the "I am directly connected" setting in FireFox.

Does anyone have any clues ???

---

### Post by ugm6hr on 2008-01-26
Not sure whether this is your problem, but ipv6 seems to cause problems for some people.

Maybe try this: [http://ubuntuforums.org/showthread.php?p=2232309#post2232309](http://ubuntuforums.org/showthread.php?p=2232309#post2232309)

---

### Post by GMP on 2008-01-26
Fixed.

Thanks a heap :) .

---

