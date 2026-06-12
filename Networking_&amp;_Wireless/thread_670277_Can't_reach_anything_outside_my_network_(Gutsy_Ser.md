---
title: "Can't reach anything outside my network (Gutsy Server ed.)"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by Submoose on 2008-01-17
I've just installed my Ubuntu server ed., and installed the network card drivers (that was a _horrible_ task to do). Now I can only ping my router and I can remotly control my server using SSH. But I can't reach the internet.
```
administrator@Betty:/$ wget http://hardware.no/
--16:15:57--  http://hardware.no/
           => `index.html'
Resolving hardware.no... failed: Temporary failure in name resolution.
```
It looks like it can find the site, but it can't download anything. The same kind of error comes when I try to run for example:
```

apt-get update

```
If anyone knows how to get it to work I'd be very happy :)

---

