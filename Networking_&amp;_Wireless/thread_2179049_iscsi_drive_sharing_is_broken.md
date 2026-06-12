---
title: "iscsi drive sharing is broken"
date: 2013-10-06
forum: Networking &amp; Wireless
---

### Post by pinus on 2013-10-06
Well, I thought it would be a good idea to put the backup drive into my "server" and share it via iscsi. Both boxes are Ubuntu 12.04, this has to work without trouble. The reality is different. There are tutorials to install, but they all do not work.

[FONT=Courier New]iscsiadm  -m discovery -t st -p benjamin -d 9[/FONT]

produces 

[FONT=Courier New]iscsiadm: connection to discovery address 192.168.xxx.yyy failed[/FONT]

I already tried to validate if the scsitarget really runs. I started is with debug flag and it tells me that there are two targets configured. I can also connect via telnet the specified port. But what realy sucks is the logging. You have to go into the daemon start procedure to get at least some output. For me it seems that the target is available.

But on the other hand iscsiadm could'n see it. And the unclassified dusty bugs in launchpad aren't to promising.

Has somebody managed to get that running, client and server from Ubuntu 12.04?

---

