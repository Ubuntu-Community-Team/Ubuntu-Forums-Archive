---
title: "Network misconfigured."
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by hornetster on 2008-04-09
I tried to install several VPN packages yesterday, and couldn't get anything to work, but have now got the prob where my networking is stuffed! When installing the packages, got some sort of error re ipsec (and didn't read it properly....!!) but since then, networking IS working (sort of), as in I can ping local addresses, but can't do anything else.... Can't web into anything (ie my router), or VNC to another machine, which I could before. Gateway and DNS etc seem to be setup OK, and everything still works for other machines, and also for Windows on this machine. Obviously there is some sort of a config prob with routing or something, but I can't work it out.....

Please help!
I have recently moved from Suse (but may move back...... :-( )

John.

And another question: in Suse, the ifstatus command returns most network info (similar to ipconfig /all in win....) Is there a similar command in Ubuntu??

---

### Post by prshah on 2008-04-09
> **hornetster said:**
> 
And another question: in Suse, the ifstatus command returns most network info (similar to ipconfig /all in win....) Is there a similar command in Ubuntu??

```
ifconfig
``` or, if specifically wireless ```
iwconfig
```

---

### Post by hornetster on 2008-04-09
Thanks, and yes I know that, and according to ifconfig everything is OK. As I said, local network is pinging, but that is all..... (also, ifconfig doesn't give you the complete network info: ip, dns,dhcp, host, domain, etc, etc)

---

### Post by hornetster on 2008-04-09
In reply to my own message, have now sorted it (thanks...). Basically checked the modified date on all the stuff in /etc, and anything that had been changed around the time the prob began, and looked vaguely networky/firewally, I moved to a different location. Then did a reboot, and everything works fine!! :-) I suspect it was an application called eBox, which I suspect was installed when I was adding the VPN stuff. 
Yep, I know I could have killed a lot more than I did, but, hey, the next option was a rebuild!

---

