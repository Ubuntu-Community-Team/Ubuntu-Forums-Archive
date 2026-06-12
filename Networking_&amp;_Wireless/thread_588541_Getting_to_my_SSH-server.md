---
title: "Getting to my SSH-server"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by Skerit on 2007-10-23
I really have thé most backwards router in human history, I believe ... (Usrobotics 9108 )

After weeks of trying to get my router accept my SSH-session while I'm on another location, I finally found the problem ... it was buggy firmware! I could open up any port, the router wouldn't care. (Checking for a firmware update would always give me a big fat NO, and then I took a "manual" look)

Anyhoo, while the ports finally open up (thanks to those virtual servers) I still can't connect to my ssh server!

At work, they block most ports (duh, they try to prevent this, lol) Now I want to redirect the 443 port to my computer's 22 port. I did this, now the only problem is, when I try to ssh my ip, it always gives me a "connection refused" when I try the 443 port. (I also tried the 110 port.)

When I try the 22 port, everything goes fine, from yet another location, not at work (where it's blocked)


Seriously, why do they bother? I've lost a hell of a lot more time on trying to get by this then anything else... :P

---

### Post by robert_pectol on 2007-10-23
I don't have an answer for why your router is not properly forwarding your port(s).  However, I do have something that you may find handy while you try to troubleshoot it from your home connection.  This is a tool I wrote to assist me in determining whether or not external connections are getting through my home router.  It gives the status of your port(s) from an external point of view.

[http://rob.pectol.com/webtoolz/portscanner.html](http://rob.pectol.com/webtoolz/portscanner.html)

Simply enter your external IP address and specify the port you want to check and then hit the scan button.  It will report back the status of your port.  :)

Hope it helps.

---

