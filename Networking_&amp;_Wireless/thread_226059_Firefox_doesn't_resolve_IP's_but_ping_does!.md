---
title: "Firefox doesn't resolve IP's but ping does!"
date: 2006-07-30
forum: Networking &amp; Wireless
---

### Post by robek on 2006-07-30
right,
this problem's to big for my small brain
over last few months i've installed ubuntu breezy than mandriva than xubuntu
on all of those distros I had the same problem - I can ping any address say google.com and it resolves fine than I can type IP obtained that way into Firefox go to google and even do some searching ;)
but when I try to use url instead of IP it doesn't work...
funny enough, on Mandriva I was able to use Konqueror without any problems (but not firefox)
now I'm running xubuntu and the problem persists...
I can't add any repositories eighter as the address ar not being resolved...
computer is a part of the network
and resolv.conf looks like this
nameserver 192.168.0.254
192.168.0.254 being my router

any input much appreciated

---

### Post by rupesh on 2006-07-31
try following postings. it might help u :-
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 
[http://www.ubuntuforums.org/showthread.php?t=222817](http://www.ubuntuforums.org/showthread.php?t=222817)

all the best..

---

### Post by robek on 2006-07-31
Thanks a lot
disabling IPv6 in Firefox did the job
apt-get and others still don't work
from other posts it looks like its D-Link router issue
so I'll have a look into that

---

### Post by mips on 2006-07-31
Besides disbaling ipv6 in firfox did you do it system wide ?

---

### Post by rupesh on 2006-07-31
heyyy got the solution on this finallyy......
follow the posting
[http://www.ubuntuforums.org/showthread.php?t=225734](http://www.ubuntuforums.org/showthread.php?t=225734)
hope it will work with u also.. best luck ....

---

