---
title: "can not shutdown as network manager's problem"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by aixilin on 2008-11-26
I just install RTAI(real time linux) on Ubuntu 8.04. After that I can not shutdown my computer and it gives me:
"Network Manager: nm-hal-deinit():libhal shutdown failed-Did not receive a reply. Possible causes include: the remote application didn't send a reply . the message bus security policy blocked the reply. the reply timeout expired, or the network connection was broken."


I dont know too much about network manager. 
Is there anybody having same problem or method to solve it???

tks

---

### Post by SpaceTeddy on 2008-11-26
i've been having that problem for about a year... it never bothered me tho, since most of the time it does shut down... nm has been crashing for me ever since i got 7.04 on shutdown... Usually i just have to wait.
A fix would be nice, nonetheless...

---

### Post by SaberCat on 2009-04-21
I recently reinstalled ubuntu 8.04 on my Dell Inspiron 1501 laptop (had too much network trouble with 8.10 and went back to 8.04!) and experienced the same problem (it wasn't there in a previous 8.04 install maybe a year earlier). I found a workaround for my case:

Under: System|Administration|Services|
Uncheck: Power management (acpid)

Now the system shuts down completely - including power shutoff. From all the postings I read on the subject, I gather that the problem is related to a NewtworkManager bug and its relation to the ACPI power management system. The above workaround disables the startup of the ACPI daemon (I assume!) and that seems to solve the problem. I don't know what other side-effects not running acpid has. So be warned...

Here's part of the error message I was getting before I applied the workaround:

NetworkManager: <WARN> nm_hal_deinit(): libha1 shutdown failed - Did not receive a reply. Possible causes include:...

---

