---
title: "Network connection is suddenly spotty"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by IAmMe1 on 2008-03-16
I've been running Ubuntu for about 6 months now, and I haven't had any issues with my Internet connection. As of about Wednesday, however, my connection has been very, very slow at random intervals, and then I'll lose the connection entirely. Sometimes it loses my wireless network connection, but usually it doesn't until I reset the connection, in which case I will sometimes lose the network entirely and sometimes it will reconnect and work perfectly.

I really don't have any idea where to start figuring out the problem, does anyone have suggestions as to how I could diagnose it? Let me know what information I should provide, I'll be happy to, but I just haven't worked with this very much and thus don't know what commands to run to diagnose the problem.

Thanks.

---

### Post by Suparious on 2008-03-17
try doing a few simple command-line tests, like ping your gateway for awhile to see if there is packet loss. Then ping a few external things (like google.ca and maby your ISP's home page). If you get packet loss to external things but not to your gateway, then you have a problem with your internet service. Otherwise the issue is hardware/software on the user-end.

CHECK YOUR CABLES! This has always been a frustrating troubleshooting step if you assume the physical stuff is good. Also going under the desk (or wherever) and unplug everything, then reconnect all your gear in a neat and organized way is the long way to ensure all your connections are not related to the problem.

Lastlly, depending on your knowlege of your own hardware; have a look through /var/log/messages and /var/log/syslog after a reboot and see if you find any errors. If you do, you may search the forums for posts about those errors also.

---

