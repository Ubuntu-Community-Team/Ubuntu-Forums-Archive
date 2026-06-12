---
title: "Any Maintained Network Traffic Reporting Software Available?"
date: 2015-05-29
forum: Networking &amp; Wireless
---

### Post by CharlesT423 on 2015-05-29
Hello,

  I'm trying to find some software that can do traffic monitoring for my network via the monitor port of my switch.  I want to be able to get some basic traffic graphs of what's going through the network at any point in time (MRTG/Cacti style stuff) plus be able to see who the bandwidth hogs are (top 10-20 bandwidth users by IP).  I've been looking around and I've found packages like pmacct and bandwidthd, but they seem to no have been abandoned with no activity in the past 10 years.  Is there anything out there that will do this for a network of 200-300 machines, not just a single Linux box?  I don't think Cacti can do "top X by usage" style graphs...

---

### Post by SeijiSensei on 2015-05-30
Take a look at ntop: [http://www.ntop.org/](http://www.ntop.org/)

---

