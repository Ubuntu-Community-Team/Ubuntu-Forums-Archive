---
title: "intermittent ethernet connection - Ubuntu 16.04 LTS, Dell Optiplex 755"
date: 2017-11-18
forum: Networking &amp; Wireless
---

### Post by gebseng on 2017-11-18
Hello everyone on the forum,

I am running Ubuntu 16.04 LTS on a Dell Optiplex 755. The PC is connected via ethernet, no WIFI. The ethernet connection show up as "Wired Connection 1" in network status on the top bar.

However, this ethernet connection disconnects every few minutes, mostly without a warning. In network status, the connection shows up as still established. I have to click "Disconnect" and then again "Wired Connection 1" to get it going again. But after a few minutes, it disconnects again, without notification.

I'm pretty sure it's not a hardware problem, since I was running the same PC with the same ethernet hardware under Windows 7 without any problems. For extra confirmation,I also tried another cable.

It would be great to get some input from you on that matter,

thanks,

geb

---

### Post by ubname on 2017-11-18
> **gebseng said:**
> Hello everyone on the forum,

I am running Ubuntu 16.04 LTS on a Dell Optiplex 755. The PC is connected via ethernet, no WIFI. The ethernet connection show up as "Wired Connection 1" in network status on the top bar.

However, this ethernet connection disconnects every few minutes, mostly without a warning. In network status, the connection shows up as still established. I have to click "Disconnect" and then again "Wired Connection 1" to get it going again. But after a few minutes, it disconnects again, without notification.

I'm pretty sure it's not a hardware problem, since I was running the same PC with the same ethernet hardware under Windows 7 without any problems. For extra confirmation,I also tried another cable.

It would be great to get some input from you on that matter,

thanks,

geb

I'm running the same, never had such problem so some hardware problem is probable,
some workaround you can try that came to my mind:

disable ip6, configure a static ip, maybe the IP conflict with some othe device?

---

### Post by gebseng on 2017-11-20
> **ubname said:**
> I'm running the same, never had such problem so some hardware problem is probable,
some workaround you can try that came to my mind:

disable ip6, configure a static ip, maybe the IP conflict with some othe device?

Thanks for the suggestion! I already thought of that, but to no avail. Maybe I'll just add a network card and see if that works.

best,

geb

---

