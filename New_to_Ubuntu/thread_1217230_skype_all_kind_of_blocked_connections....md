---
title: "skype all kind of blocked connections..."
date: 2009-07-19
forum: New to Ubuntu
---

### Post by heyyy on 2009-07-19
whenever i use skype i see all kinds of blocked connections in the firestarter... although skype seems to work just fine.
there is something else since i've installed skype i seem to have connections to adresses like "...163-163.static.quiettouch.com" even when i havent ran skype at all since i booted!
why is this happening?

---

### Post by 3rdalbum on 2009-07-19
> **heyyy said:**
> whenever i use skype i see all kinds of blocked connections in the firestarter... although skype seems to work just fine.
there is something else since i've installed skype i seem to have connections to adresses like "...163-163.static.quiettouch.com" even when i havent ran skype at all since i booted!
why is this happening?

Skype uses peer-to-peer traffic to carry phone calls. It is normal to have attempted connections into your machine when running Skype. (not sure why they even bother... don't most people use a firewall?)

As for your other question, that's my main gripe with Firestarter*; it logs so much that people get worried when they see attempted connections. They think their computer is under attack or something.

With the amount of malware running on Windows machines, every IP address gets tested by every bit of malware to see if there's a viable target residing at that address. Everyone gets this traffic. It's not nice, but it's completely normal. Also note that if you connect to the Freenode IRC server (which the official #ubuntu resides on) you will get benign port scans from Freenode; this is normal too.

* Yes, verbose logs are a good thing and I don't actually want the Firestarter developers to remove the logging; Firestarter is more of a sysadmin frontend than an end-user frontend, and as such the logs are useful. But I do think that new Ubuntu users should be encouraged to use UFW or gUFW as the firewall frontend rather than Firestarter, because UFW doesn't scare people with logs :-)

---

### Post by heyyy on 2009-07-19
ok but can you explaine me this: 
> something else since i've installed skype i seem to have connections to adresses like "...163-163.static.quiettouch.com" even when i havent ran skype at all since i booted!

i mean this is definately not normal...   ?

---

