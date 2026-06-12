---
title: "pop email dropping my network connection"
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by clivel on 2006-11-13
I have networking, both wireless and wired up and working most of the time, that is until I try to check my email.

I am running Edgy, and I have tried with a number of routers, both wireless and wired, almost every time Evolution tries to do a POP connection my computer seems to lose the ability to resolve names.
I am using the NetworkManager applet for switching networks, this shows the connection still active. The only way I can restore my connectivity seems to be to cycle power on the router.
Any advice would be appreciated.
Thanks,
Clive

---

### Post by stream303 on 2006-11-14
Hmm..  have you placed your isp's dns nameservers in the router's setup page?

What does /etc/resolv.conf show?  Does it contain your isp's nameservers or just the router nameserver (dns forwarder actually)

---

### Post by clivel on 2006-11-14
Hi Stream 303,
This is the contents of my /etc/resolv.conf:

search localdomain
nameserver 64.59.144.90
nameserver 64.59.144.91

I haven't modified it myself.  64.59.144.xxx belongs to my ISP when connected from home (where I currently am). I haven't had a single drop out tonight running for a few hours, however last night, and at work today, it dropped out almost every time I tried to check my email.
At work I was using the office wired network, as well as the four open wireless points somewhere in the building. The only way I could restore connectivity was by cycling the power on the router, which unfortunately wasn't possible with the open wireless points. I will have to check the resolv.conf tomorrow when I get to work, to see if it is updated. As this is a laptop, I don't want to have to manually edit my resolv.conf every time I am at a new location, I would have expected it to be updated automatically.
Thanks,
Clive

---

