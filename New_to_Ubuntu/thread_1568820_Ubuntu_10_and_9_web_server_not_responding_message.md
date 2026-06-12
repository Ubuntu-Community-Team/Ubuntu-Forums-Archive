---
title: "Ubuntu 10 and 9 web server not responding message"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by becketma on 2010-09-05
Ubuntu 8 easily links to the web sites I frequent.
I tried 10 but it only will link to two of the sites I use, one of them is here--it "times out" on all of the others, like when running a Google search.
I tried 9 but with the same results.

My internet is slow, averaging around 28kbs for downloads.

It there a thread where I can read about why this happens, I assume a timing issue, if the web site doesn't respond within a specified time, almost immediately right now, it displays the server not responding message.

Thanks
Bob

---

### Post by sandyd on 2010-09-05
> **becketma said:**
> Ubuntu 8 easily links to the web sites I frequent.
I tried 10 but it only will link to two of the sites I use, one of them is here--it "times out" on all of the others, like when running a Google search.
I tried 9 but with the same results.

My internet is slow, averaging around 28kbs for downloads.

It there a thread where I can read about why this happens, I assume a timing issue, if the web site doesn't respond within a specified time, almost immediately right now, it displays the server not responding message.

Thanks
Bob
Try doing this.
go to "about:config"
in the firefox address bar

type in "timeout" in the search thingy.
change the "network.*" values to a higher number

---

### Post by becketma on 2010-09-06
I've stumbled around looking for the FireFox address bar but have only succeeded in disabling Mozilla by typing in "about:config" in its "command prompt".

It also seems as if I can't figure out how to turn my computer off from Ubuntu 10?

Best from tucson
Bob

---

### Post by jmlm-1970 on 2012-02-13
The solution for some URL return timeout error is in firewall settings.

Just disable the following, in firewal preferences (menu Edit/Preferences/Advanced Options):

block broadcasts from external network
block broadcasts from internal network
block traffic from reserved addresses on public interfaces

Have fun,
João Moreira.

---

