---
title: "Lost my wired internet connection"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by rifferte on 2007-11-03
Last night upon logging into my new Ubuntu 7.10 system, I quickly realized that I can no longer connect to the internet via my wired desktop connection.

Some background:

1) I have had 7.10 running without issue since it was released (7.10 was installed new).
2) The machine dual boots Windows XP. I have no issue with my connection on Windows.
3) Initially - my wired connection was set up and working in roaming mode, so I switched it to DHCP after I couldn't connect any longer. That didn't work either.
4) Looking at network manager, it is apparent I have no connection (i.e. no ip address etc).

Also, the kern, debug and syslog logs all have the following:

[FONT="Courier New"]
Nov  2 22:47:40 Ubuntu kernel: [  432.937436] NETDEV WATCHDOG: eth0: transmit timed out
....
Nov  2 22:47:28 Ubuntu kernel: [  420.953138] eth0: Tx queue start entry 4  dirty entry 0.
Nov  2 22:47:28 Ubuntu kernel: [  420.953142] eth0:  Tx descriptor 0 is 0008203c. (queue head)
Nov  2 22:47:28 Ubuntu kernel: [  420.953145] eth0:  Tx descriptor 1 is 0008203c.
Nov  2 22:47:28 Ubuntu kernel: [  420.953148] eth0:  Tx descriptor 2 is 0008203c.
Nov  2 22:47:28 Ubuntu kernel: [  420.953151] eth0:  Tx descriptor 3 is 0008203c.
Nov  2 22:47:43 Ubuntu kernel: [  435.933532] eth0: Transmit timeout, status 0d 0000 c07f media 
10.
....
Nov  2 22:43:46 Ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
[/FONT]

So - its obvious that DHCP isn't working - but I have no idea why (especially since this was working like three days ago).

Does anyone have any ideas or troubleshooting hints?

Thanks,

 - Ron

---

### Post by mmikelst on 2007-11-04
I have exactly this problem, same error messages, etc. I'm curious, what are your Network Tools-->Devices options? I'm running a laptop with both a wired and wireless connection and I could connect w/ ubuntu until this morning, and now I have a fourth option (not sure where it came from) labeled "Ethernet Interface (eth0:avahi)." Anything similar on your end?


-M

---

### Post by mmikelst on 2007-11-04
*Does the triumphant "found solution" dance*

Okay. 

Here are the links for the problem I found when I dove into the forums. 

[http://ubuntuforums.org/showthread.php?t=580773&highlight=eth0%3A+Transmit+timeout](http://ubuntuforums.org/showthread.php?t=580773&highlight=eth0%3A+Transmit+timeout)
[http://ubuntuforums.org/showthread.php?t=533488&highlight=eth0%3A+Transmit+timeout&page=2](http://ubuntuforums.org/showthread.php?t=533488&highlight=eth0%3A+Transmit+timeout&page=2)
[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

Depending on exactly what went wrong with yours, ONE of these should fix it. The way I fixed my own personal issue was following this link [http://gentoo-wiki.com/HARDWARE_RTL8168](http://gentoo-wiki.com/HARDWARE_RTL8168) (embedded inside one of the above links) and changed my wake-on-lan settings within windows to enabled (per the first paragraph). That fixed the issue beautifully for me, and now I'm just trying to undo the damage I did to my system trying to locate the problem in the first place. Good luck with your issue, and I hope this helps!

-M

---

