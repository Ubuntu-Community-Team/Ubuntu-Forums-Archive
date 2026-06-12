---
title: "ushare - interface eth0 is down."
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by wunder on 2008-08-29
I recently installed and configured ushare to stream to my xbox360.  Everything seems to be working fine, however everytime I start up ushare I get the startup error that "Interface eth0 is down."

I can run the web interface without any problems.  It streams without any problems, but just for my own peace of mind, is there any reason that this error would be popping up?  Is there something I can change?

I attempted to search for this, but couldn't find anything, and please understand that i'm pretty new at linux.  Thank you all for any help that you can give.

---

### Post by lolx on 2010-07-07
Hi 

That's because one of your configured ports is already in use. Ether the web or the telnet port is in use by another program (is apache running?) .. that why ushare complains about the interface down... I know, the message is not very smart. 
Try disable web and telnet you will see the error is gone 

cheers
lolx

---

