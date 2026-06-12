---
title: "Slow"
date: 2006-07-31
forum: Networking &amp; Wireless
---

### Post by Dylan103 on 2006-07-31
Ok, I just installed ubuntu and saw that my internet wasn't working.
So, I went to System > Administration > Networking > DNS
And I added 192.168.1.1
Then, my internet started to work, but very slow. About 14 seconds to load [www.mozilla.com](www.mozilla.com)

What should I do?

---

### Post by wieman01 on 2006-07-31
You probably need to disable ipv6. Try this:

[http://www.ubuntuforums.org/showthread.php?t=218733]("http://www.ubuntuforums.org/showthread.php?t=218733")

This will make all the difference.

---

### Post by Dylan103 on 2006-07-31
hmm still not working, should I edit anything in networking? Change the ip?

---

### Post by rupesh on 2006-07-31
follow this threads to get more on it:--

[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 
[http://www.ubuntuforums.org/showthread.php?t=222817](http://www.ubuntuforums.org/showthread.php?t=222817)
 hope it will help u.

---

### Post by wieman01 on 2006-07-31
> **Dylan103 said:**
> hmm still not working, should I edit anything in networking? Change the ip?

Have you disabled the ipv6 module and configured Firefox (if that's the browser you are using) accordingly?

---

### Post by Dylan103 on 2006-07-31
Yeah, its a bit faster but not as fast as windows. Oh well, hope I can get it. Thanks for the help.

---

### Post by mips on 2006-07-31
edit your resolv.conf file and change the name servers to that of your ISP. IF you have a nameserver using your routers IP address hash '#' it out.

See if it makes a difference.

---

### Post by Dylan103 on 2006-07-31
Yeah that worked thanks

---

