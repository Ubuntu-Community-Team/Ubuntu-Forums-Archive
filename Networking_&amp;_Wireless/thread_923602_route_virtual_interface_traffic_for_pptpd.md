---
title: "route virtual interface traffic for pptpd"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by anaggressivemonkey on 2008-09-18
Hi,

I have a virtual interface eth0:1 that i'm using for incoming ppp users.   I want to be able to route out all traffic out via eth0 so those incoming users can access the the rest of the net.

I'm stuck as to whether i need to do put in a route to do this, or if i can do this in iptables.

Any suggestions or recommendations?


Thanks

---

### Post by gentoo42 on 2008-09-26
I was having this exact same issue.  I got pptpd setup and working, but was unable to access anything while connected. I found the solution to be enabling IP forwarding, and basically followed this guide:

[http://www.ducea.com/2006/08/01/how-to-enable-ip-forwarding-in-linux/](http://www.ducea.com/2006/08/01/how-to-enable-ip-forwarding-in-linux/)

hope this helps someone out with the same issues, none of the pptpd setup guides seemed to include this information.

---

