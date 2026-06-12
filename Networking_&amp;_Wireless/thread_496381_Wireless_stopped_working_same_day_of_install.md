---
title: "Wireless stopped working same day of install"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by topgun98 on 2007-07-09
I installed Ubuntu for the first time today.  It auto-detected my wireless card and wired nic, got a DHCP lease, and everything worked great without a problem.  Since then I allowed the updater application to do what I assume is an apt-get upgrade, which included a new kernel.  Now I'm able to see the wireless networks around me, but I'm unable to connect.  iwconfig indicates that no association occurs at all.  In other words, it's not a problem getting a DHCP lease.

Thanks in advance to anyone willing to help!

---

### Post by corax on 2007-07-09
Hi !

Can you be more specific on your wireless card (modell, manufacturer, chip, ...) ?

Are you using network manager ?

Is your wireless and wired network connected at the same time (not necessarily to the same router ...) ?

Which distribution are you using ? Feisty, Dapper, ...

Are you using encryption on your wireless interface ?

...

Bye

---

### Post by Keen101 on 2007-07-09
yes, I have had LOTS of problems with network manager. I don't even use it anymore. I just use network admin.

If you are using network manager (the little applet on the desktop), and have it set to "roaming mode" in network admin, then you probably are experiencing a bug. As my friend who works for Launchpad once told me: "forget that roaming mode even exists! It has a bug"


now in my experience "roaming mode" does work, but not if network manager is installed.


Good Luck :)
-Keen101

p.s. do please try and give us more info. That always helps. :)

---

