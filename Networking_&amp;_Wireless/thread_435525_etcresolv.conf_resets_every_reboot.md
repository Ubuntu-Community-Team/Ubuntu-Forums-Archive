---
title: "/etc/resolv.conf resets every reboot"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by mmarkvillanueva on 2007-05-07
Hi,

I cannot connect to the Internet via my ADSL as a normal user. But when I try to boot Ubuntu using recovery mode, I can connect to the net afer pppoeconf. I noticed that in this mode I am "root" and also the file /etc/resolv.conf contains the correct DNS servers.

What I did is that I rebooted ubuntu and login as a normal user. I copied the DNS servers taken from /etc/resolv.conf in recovery mode to the /etc/resolv.conf that I have when I boot ubuntu normally. After running pppoeconf, I can now connect to the Internet.

But the problem is that everytime I reboot the PC, the /etc/resolv.conf resets. So I need to edit this file everytime I want to conenct to the Internet and re-run pppoeconf.

I've tried two ways of editing /etc/resolv.conf (using text editor by manually editing the file and by using System->Administration->Networking)

How do I prevent /etc/resolv.conf from resetting. And also how do I load pppoe during boot time. So that once I login in X I dont need to run sudo pon dsl-provider. 

Thanks!

---

### Post by diepruis on 2007-05-07
```

sudo chattr +i /etc/resolv.conf

```

This makes the file immutable. Only the super user or certain processes may remove this setting. This fixed the problem on my computer.

---

