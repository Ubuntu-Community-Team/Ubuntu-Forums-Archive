---
title: "Zoom 56k modem won't dial"
date: 2005-07-27
forum: Networking &amp; Wireless
---

### Post by igiugik on 2005-07-27
I have a 56k dial up modem I have been using for years with various flavors of Linux, infact it's currently working fine with Debiaan, Fedora Core, Mandrake, and Xandros on other partitions.  Interestingly, the modem displays the exact same problem on both Ubuntu and Mepis, both of which I recently loaded to give them a whirl.  When you hit connect on kppp after configuring dialup, it finds the modem ("Modem ready") then says "Initializing modem"  and continues to say that forever.  It is not dialing, just trying to initialize.  Log shows no activity, just "Waiting for OK".  Tried duplicating /etc/options from other working Linuxes on other partitions...no joy.

Followed the Ubuntu Modem Howto, but it just uses pppconfig and yields the same results.  

Anyone have any ideas.  I'm stumped for now but will check some logs tomorrow after I get some sleep.

---

### Post by igiugik on 2005-07-28
Well - I'll answer myself.  New info.  Discovered by reviewing dmesg that the OS is selecting 2 devics for the single modem - ttyS0 and ttyS14.  If I try to dial using ttyS0, problem is as stated above - screen says "initializing modem" and stays there and does not dial.  If I try to dial through ttyS14, modem dials, but hangs at the very end of the communication with the ISP with a ppp Error 1, which in the man page gives no helpful info whatsoever.  Tonight I'll start going through logs to see if I caan find more pointers to the problem.  If anyone has seen two /dev's grab on to a single device, I'd love to hear from you.

---

