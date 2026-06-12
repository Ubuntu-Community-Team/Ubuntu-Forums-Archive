---
title: "Squid Startup Error"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by Slinger on 2007-03-28
Greetings all.  First, my apologies if this is not the proper forum.

I have a fresh install of 7.04, granted I know it is beta.  I installed Squid through synaptic and all went fine.  Everything was working for a couple days and then when I rebooted next, upon startup squid will not run.

I can start the process and all looks good.  However, doing a netstat -an does not show the machine listening on 3128.  I then tailed messages while starting it and got the following:

[I]Mar 27 19:00:02 Nightwind squid[5849]: Squid Parent: child process 5851 started
Mar 27 19:00:02 Nightwind squid[5849]: Squid Parent: child process 5851 exited due to signal[/I] 

So it starts and then fails.  I have done some research via google and the answers I got for "signal 6" are very vague.  Mainly what is stated is that it could be a bad squid.conf or bad hardware.

The squid.conf is what I was using previously.  Mainly vanilla from the install with the only addition being the visible_hostname.  My hardware is fine, everything works well - ran fsck on the partitions.  I see no visible errors for any hardware so I highly doubt that is the issue.

Just wanted to drop a line to check if anyone has had similar issues.  I could post my squid.conf file, though too big and as stated, nothing other than visible_hostname was changed.  Historically I have had no issues in the past using it as is.

Any thoughts?

---

