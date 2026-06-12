---
title: "Monitor network packets"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by rbowen1 on 2011-07-13
Is there a way to check sent/receive network packets by eth0?    It shows connected but I want to see the actual sent/receive packet count increasing.     I am running Natty, Ubuntu 11.04

Command line code would be preferred.   

Any ideas or assistance is appreciated.

---

### Post by BitJunkie on 2011-07-13
I'm not at my Natty machine to check for sure, but it seems like there's a netstat option that will show packet counts. Or for more detail, maybe try tcpdump.

---

### Post by The Cog on 2011-07-13
I would normally use **ifconfig eth0** for this. Or **watch ifconfig eth0**. For prettier text-mode, perhaps **iftop** (it's in the repos).

---

### Post by aktiwers on 2011-07-13
Or look into netstat

---

### Post by alphacrucis2 on 2011-07-13
If you want to see all details of all packets use wireshark. It's in the universe repo.

---

### Post by rbowen1 on 2011-07-14
My thanks to all that replied.    After checking the suggestions offered, I did a little more research and found that nethogs is what I was looking for.   More detailed info is availible for anyone else interested at this link.   
[http://www.ubuntugeek.com/nethogs-net-top-tool-grouping-bandwidth-per-process.html](http://www.ubuntugeek.com/nethogs-net-top-tool-grouping-bandwidth-per-process.html)

Thanks again to Ubuntu community.   
Solving this thread

---

