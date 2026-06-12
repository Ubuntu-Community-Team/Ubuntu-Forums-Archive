---
title: "OpenSSH Client stopped working"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by haz2a on 2007-04-19
I have several PCs which SSH into a database server. One Linux PC running Xubuntu 6.06 with openssh-client v1:4.2p1-7ubuntu3.1, which was working perfectly well up to yesterday, suddenly stopped connecting to the server. All the other PCs (including those running Ubuntu 6.06) can still SSH in OK. The faulty PC can still access the internet OK, and I can SSH into the openssh-server on the faulty PC. I just can't SSH out of the faulty PC, either from Gnome Terminal or from the console, either as the usual user, or as the admin user.  Using 'ssh -v' it hangs silently at:-  ~ debug1: Connecting to ... port 22  Then after about 10 minutes it exits with 'Connection timed out'.  I've tried removing openssh-client and openssh-server including config files, then reinstalling - made no difference.  I've tried after disabling the firewall in Firestarter - same.  Can anyone suggest anything else I could try or test?

---

### Post by kidders on 2007-04-20
Hi there,

This is most likely a networking issue. It could be due to DNS problems, an IPv6 misconfiguration, or something like that. Did this issue coincide with any changes you may have made to your system/network? Since your problem seems to only affect SSH, it *could* be that the server is having some odd problem resolving the address of that specific client, for some reason.

My suggestions are very vague (sorry for that), but I'd say your problem is probably being caused by something little ... so it might be difficult to spot.

---

